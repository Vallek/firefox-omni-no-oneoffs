# firefox-omni-no-oneoffs
Disables search engines buttons (aka one offs) from Firefox urlbar (aka omnibar).

**How to**: replace omni.ja file in your \Mozilla Firefox\browser folder with this copy.

**If you want to edit it yourself**: 
1. Open omni.ja as folder (I use Total Commander for that)
2. Find modules\UrlbarSearchOneOffs.jsm
3. Open it (I use Notepad++, vs code didn't save properly inside archive). DO NOT TOUCH POPUP.
4. Find 
```
  enable(enable) {
    if (enable) {
      this.telemetryOrigin = "urlbar";
      this.style.display = "";
      this.textbox = this.view.input.inputField;
      if (this.view.isOpen) {
        this._rebuild();
      }
      this.view.controller.addQueryListener(this);
    } else {
      this.telemetryOrigin = null;
      this.style.display = "none";
      this.textbox = null;
      this.view.controller.removeQueryListener(this);
    }
  }
```
5. Copy second half after `else` inside brackets {}.
6. Paste it instead of first half. Like that:
```
  enable(enable) {
    if (enable) {
      this.telemetryOrigin = null;
      this.style.display = "none";
      this.textbox = null;
      this.view.controller.removeQueryListener(this);
    } else {
      this.telemetryOrigin = null;
      this.style.display = "none";
      this.textbox = null;
      this.view.controller.removeQueryListener(this);
    }
  }
```
7. Save file, close it. NOW YOU CAN CLOSE POPUP.
8. Say Ok in another popup. If you don't see it you did something wrong. 
9. Replace file in Firefox folder using Admin rights.
10. Start Firefox with -purgecaches option one time.

upd1: This fix started to cause troubles with urlbar in version 85. 

upd2: Fixed it for version 91!

upd3: They broke it some time ago. It now breaks the browser! I'm looking into it.

upd4: Fixed it for **version 102**!