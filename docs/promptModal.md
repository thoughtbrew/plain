### Prompt modal replacement

`<2Kb`

```
promptModal('Please enter your new password.', (message) => {
  // ...
}, {password: true});
```
#### JS

```
function promptModal(msg, cbk, opts) {
	cbk = cbk || function() {};
	opts = opts || {};
	const dc = (el) => document.createElement(el);
	const wrapper = dc('section');
	const backing = dc('div');
	const modal = dc('div');
	const message = dc('div');
	const input = dc('input');
	const footer = dc('div');
	const cancel = dc('button');
	const okay = dc('button');
	wrapper.className = 'prompt-modal wrapper';
	backing.className = 'backing';
	modal.className = 'modal';
	message.className = 'message';
	message.innerHTML = msg;
	input.tabIndex = 100;
	okay.tabIndex = 101;
	cancel.tabIndex = 102;
	okay.innerHTML = 'Okay';
	cancel.innerHTML = 'Cancel';
	if (opts.password) {
		input.type = 'password';
	}
	wrapper.appendChild(backing);
	wrapper.appendChild(modal);
	modal.appendChild(message);
	modal.appendChild(input);
	modal.appendChild(footer);
	footer.appendChild(cancel);
	footer.appendChild(okay);
	document.body.appendChild(wrapper);
	function clean() {
		input.removeEventListener('keyup', onInputKeyup);
		okay.removeEventListener('keyup', onOkay);
		okay.removeEventListener('click', onOkay);
		cancel.removeEventListener('keyup', onCancel);
		cancel.removeEventListener('click', onCancel);
		document.body.removeChild(wrapper);
	}
	function onOkay(e, bypass) {
		console.log(e.keyCode, e.charCode, e);
		if (bypass || e.type === 'click' || [13, 32].indexOf(e.keyCode) > -1) {
			const val = String(input.value);
			cbk(val);
			clean();
		}
	}
	function onCancel(e, bypass) {
		if (bypass || e.type === 'click' || [13, 32].indexOf(e.keyCode) > -1) {
			cbk(null);
			clean();
		}
	}
	function onInputKeyup(e) {
		if ([13].indexOf(e.keyCode) > -1) {
			onOkay(e, true);
			return;
		}
		if ([27].indexOf(e.keyCode) > -1) {
			onCancel(e, true);
		}
	}
	input.addEventListener('keyup', onInputKeyup);
	okay.addEventListener('keyup', onOkay);
	okay.addEventListener('click', onOkay);
	cancel.addEventListener('keyup', onCancel);
	cancel.addEventListener('click', onCancel);
	input.focus();
}
```

#### CSS

```
.prompt-modal.wrapper {
  position: absolute;
  top: 0px;
  bottom: 0px;
  left: 0px;
  right: 0px;
  z-index: 2000;
}

.prompt-modal .backing {
  width: 100%;
  height: 100%;
  background: rgba(0,0,0,0.3);
}

.prompt-modal .modal {
  padding: 32px;
  position: absolute;
  top: 240px;
  left: 0px;
  right: 0px;
  margin: 0 auto;
  width: 400px;
  min-height: 64px;
  background: #fff;
  border-radius: 2px;
  box-shadow: 0px 0px 2px rgba(0,0,0,0.3);
}

.prompt-modal .message {
  margin-bottom: 16px;
}

.prompt-modal input {
  width: 100%;
  height: 32px;
  border-radius: 2px;
  margin-bottom: 24px;
}

.prompt-modal button {
  float: right;
  width: 128px;
  height: 32px;
  border-radius: 2px;
  background: #f1f1f1;
  border: 1px solid transparent;
}

.prompt-modal button:focus {
  border-color: #2cb5e9;
  box-shadow: 0px 0px 1px rgba(0,0,0,0.1);
}

.prompt-modal button:hover {
  border-color: #ccc;
  box-shadow: 0px 0px 1px rgba(0,0,0,0.1);
}

.prompt-modal button:active {
  border-color: #2cb5e9;
}

.prompt-modal button:last-child {
  margin-right: 8px;
}
```

### Tags

`ui` `prompt` `modal`
