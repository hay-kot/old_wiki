# Python

## Utilities

### System Logger

```python
import logging
from pathlib import Path

LOGGER_LEVEL = "INFO"
CWD = Path(__file__).parent
LOGGER_FILE = CWD.joinpath("main.log")

logging.basicConfig(
    level=LOGGER_LEVEL,
    format="%(asctime)s %(levelname)s: %(message)s",
    datefmt="%d-%b-%y %H:%M:%S",
    filename=LOGGER_FILE,
)
coloredlogs.install(
    level=LOGGER_LEVEL,
    fmt="%(asctime)s %(levelname)s: %(message)s",
    datefmt="%d-%b-%y %H:%M:%S",
)

logger = logging.getLogger(__name__)

""" Logging Cheat Sheet
logger.debug("this is a debugging message")
logger.info("this is an informational message")
logger.warning("this is a warning message")
logger.error("this is an error message")
logger.critical("this is a critical message")
"""
```

### Custom Color Logger

```python
import logging
import coloredlogs

logging.basicConfig(level=logging.DEBUG, )
logging.basicConfig(format='%(asctime)s %(levelname)s: %(message)s', datefmt='%d-%b-%y %H:%M:%S')
coloredlogs.install(level='DEBUG', fmt='%(asctime)s %(levelname)s: %(message)s', datefmt='%d-%b-%y %H:%M:%S')

logger = logging.getLogger(__name__)

""" Logging Cheat Sheet
logger.debug("this is a debugging message")
logger.info("this is an informational message")
logger.warning("this is a warning message")
logger.error("this is an error message")
logger.critical("this is a critical message")
"""
```


## Notifications
### Slack Notifications

```python
from slacker import Slacker

secret = '{SECRET_KEY}' # API Key
slack = Slacker(secret)

def slack_notify(text, channel):
    slack.chat.post_message(channel=channel,
                            text=text,
                            username='Python Test',
                            icon_url='http://devarea.com/wp-content/uploads/2017/11/python-300x300.png')

# Example
slack_notify('test message', f'#{CHANEL}')
```

### Node-Red Webhook

```python
import requests
import datetime

def homeassistant_webhook(entity, message):
    BASE_URL = f"https://{HOMEASSISTANT_URL}/api/webhook/"
    URL = f"{BASE_URL}/{entity}"
    requests.post(URL, message)
    
timestr_post = datetime.datetime.now().strftime("%b %d %H:%M")    
homeassistant_webhook("script_backup_manager", f"Last Ran {timestr_post}")
```