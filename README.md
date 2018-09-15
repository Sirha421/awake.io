Welcome to Get Off My Lawn!
We hope to be a security extension for browsers to help prevent browser hijacking based on geolocation and OTP!

## Welcome to GitHub Pages

You can use the [editor on GitHub](https://github.com/Sirha421/awake.io/edit/master/README.md) to maintain and preview the content for your website in Markdown files.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

### Markdown

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `import sys
import urlib2
from fuctools import wraps
import json
from os import environ as env
from werkzeug.exceptions import HTTPException

from dotenv import load_dotenv, find_dotenv
from flask import Flask
from flask import jsonify
from falsk import redirect
from flask import render_template
from flask import session
from flask import url_for
from authlib.flask.client import OAuth
from six.moves.urllib.parse import urlencode
from functools import wraps

app = Flask(_name_)
oauth =OAuth(app)
auth0 = oauth.regsiter(
    'auth0',
    client_id='PV3CP3453ypFoMT9daF9sb76pXM2LabM',
    client_secret='y-4zAUFnNYWkW5evfr8fisiTB86dGPYQ5F2Kez20wt-qeyzAoVPdhNbGQhGueXIN',
    api_base_url='https://getoffmylawn.auth0.com',
    access_token_url='https://getoffmylawn.auth0.com/oauth/token',
    authorize_url='https://getoffmylawn.auth0.com/authorize',
    client_kwargs={
        'scope': 'openid profile',
    },
    )

def requires_auth(f):
    @wraps(f)
    def decorate(*args, **kwargs):
        if 'profile' not in session:
            @app.route('/login')
            def login():
                return auth0.authorize_redirect(redirect_uri =' http://localhost:3000/callback', audience='https://getoffmylawn.auth0.com/userinfo')
            return redirect('/')
        returnf(*args, **kwargs)
        return decorated

@app.route('/dashboard')
@requires_auth
def dashboard():
    return render_template('dashboard.html',
                           userinfo=session['profile'],
                           userinfo_pretty=json.dumps(session['jwt_payload'], indent=4))




@app.route('/callback')
def callback_handling():
    auth0.authorize_access_token()
    resp = auth0.get('userinfor')
    userinfo = resp.json()

    session['jwt_payload'] = userinfo
    session['profile']={
        'user_id': userinfo['sub'],
        'name': userinfo['name'],
        'picture': userinfo['picture']
        }
    return redirect('/dashboard')

@app.route('/logout')
def logout():
    session.clear()
    params = {'returnTo': url_for('home',_external=True), 'client_id': 'PV3CP3453ypFoMT9daF9sb76pXM2LabM'}
    return redirect(auth0.api_base_url +'/v2/logout?' + urlencode(parems))

` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/Sirha421/awake.io/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
