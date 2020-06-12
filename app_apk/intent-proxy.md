[:back:](/home)
---

## Purpose
The Android Intent Proxy is a service that runs in the background and will translate and forward incoming intents, which are directed torwards applications used within the context of ExOT. This allows us to provide an uniform intent interface to the driver, and communicate with applications that require more complex intents (budled extras).

## Sending an intent to the proxy

An intent can be sent using following command:
```
adb shell am startservice -a ch.ethz.exot.intents.IntentProxy.action.BUNDLE_EXTRAS -n ch.ethz.exot.intentproxy/.IntentProxyService [EXTRAS --ei, --es, --ez, etc.]
```

### Intent Actions
The intent proxy allows following actions:

* `ch.ethz.exot.intents.IntentProxy.action.BUNDLE_EXTRAS` -> The intent proxy will forward the intent to the specified app and bundle all given extras as Binary-Bundle.
* `ch.ethz.exot.intents.IntentProxy.action.START_APPS` -> The intent proxy send a start intent to the specified application that was created using the ExOT application library.
* `ch.ethz.exot.intents.IntentProxy.action.STOP_APPS` -> The intent proxy send a stop intent to the specified application that was created using the ExOT application library.
* `ch.ethz.exot.intents.IntentProxy.action.CONFIGURE_APP` -> The intent proxy send a configuration intent to the specified application that was created using the ExOT application library.
* `ch.ethz.exot.intents.IntentProxy.action.FORWARD`  -> The intent proxy will forward the intent to the specified app.

### Extra keys
There are a couple of special extra keys that will be interpreted by the intent proxy, all other extras will be forwarded either plain or (depending on the action) repackaged. The special extra keys are:

* `intent.action` -> This extra specifies the action in the forwarded intent.
* `intent.component` -> This extra specifies the componentn in the forwarded intent.
* `intent.flags` -> This extra specifies the flags in the forwarded intent.
* `intent.extra.key` -> This extra specifies the key that will be used for the repackaged extras in the forwarded intent.

## Example
The following intent directs the intent proxy to bundle the extras into a binary-bundle and forward them to the RepetiTouch application, which will be directed to start the replay of a trace save to the file `/sdcard/Sequences/TEST`.

```
adb shell am startservice -a ch.ethz.exot.intents.IntentProxy.action.BUNDLE_EXTRAS -n ch.ethz.exot.intentproxy/.IntentProxyService --ei "intent.flags" 20 --es "intent.component" "com.cygery.repetitouch.pro/com.cygery.repetitouch.pro.FireReceiver" --es "intent.action" "com.twofortyfouram.locale.intent.action.FIRE_SETTING" --es "intent.extra.key" "com.twofortyfouram.locale.intent.extra.BUNDLE" --es "condition" "None" --es "filename" "/sdcard/Sequences/TEST" --ei "looptimes" 1 --ei "replayspeed" 1 --ez "appendingrecord" "false" --ez "hidepanel" "false" --ez "closeafteraction" "false" --ez "silent" "false" --es "action" "Start\\\\ Replay"
```