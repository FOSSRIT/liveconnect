liveconnect
===========

`liveconnect` is a handy Python 2.7.x library for interacting with Microsoft's Liveconnect API, and for getting stuff done with SkyDrive.

## Usage

Getting authorized with `liveconnect` is easy. First, make sure you've registered your application with Microsoft, and you've got your client ID and secret handy.

```python
# assuming the Mobile/Desktop auth flow (no redirect uri needed)
import liveconnect
lc = liveconnect.LiveConnect(client_id, client_secret)
print lc.generate_auth_url(scopes=['wl.basic'], redirect_uri=None, state=None)
>>> 'https://login.live.com/oauth20_authorize.srf?state=&redirect_uri=https%3A%2F%2Flogin.live.com%2Foauth20_desktop.srf&response_type=code&client_id=client_id&scope

# then, having retrieved the auth_code from the http response
print lc.authorize(auth_code='auth_code')
>>>  {
    u'token_type': u'bearer',
    u'scope': u'wl.basic',
    u'access_token': u'access_token_123',
    u'expires_in': 3600,
    u'refresh_token': u'refresh_token_123'
  }
```

## Installation

You can install `liveconnect` from the Cheeseshop with `pip`.

    pip install liveconnect

## Requirements

`liveconnect` simply requires that the [requests](http://docs.python-requests.org/en/latest/) library be installed. Installing with `pip` will take care of this for you.

## License

`liveconnect` is released under the MIT License. See the `LICENSE` file for details.