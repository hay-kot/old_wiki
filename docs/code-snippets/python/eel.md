# Eel

This code snippet is used in conjunction with the Eel GUI framework and serves as a way to pass logging data into the web GUI while also logging on the system level. Note that you cannot include these functions underneath a class. While it works, it throws errors. 

```python
import eel
from datetime import datetime

def get_timestamp():
    dateTimeObj = datetime.now()
    timestampstr = dateTimeObj.strftime("%d-%b-%y %H:%M:%S")
    return timestampstr

def EelLogger_debug(msg):
    mode = "DEBUG"
    timestamp = get_timestamp()
    msg = f"{timestamp} {mode} {msg}"

    eel.logger(msg)
    logger.debug(msg)

def EelLogger_info(msg):
    mode = "INFO"
    timestamp = get_timestamp()
    msg = f"{timestamp} {mode} {msg}"
    eel.logger(msg)
    logger.info(msg)

def EelLogger_warning(msg):
    mode = "WARNING"
    timestamp = get_timestamp()
    msg = f"{timestamp} {mode} {msg}"
    eel.logger(msg)
    logger.warning(msg)

def EelLogger_error(msg):
    mode = "ERROR"
    timestamp = get_timestamp()
    msg = f"{timestamp} {mode} {msg}"
    eel.logger(msg)
    logger.error(msg)

def EelLogger_critical(msg):
    mode = "CRITICAL"
    timestamp = get_timestamp()
    msg = f"{timestamp} {mode} {msg}"
    eel.logger(msg)
    logger.critical(msg)
```

```javascript
eel.expose(logger);
function logger(msg) {
  const outputNode = document.getElementById("log-output"); // Text Output Element
  outputNode.value += msg + "\n";
  outputNode.style.height = outputNode.scrollHeight + 10 + "px";
}
```
