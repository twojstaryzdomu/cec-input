# cec-input
SystemD service for executing commands with CEC / remote control

## How to run & configure
1. Install `cec-utils` with `# apt-get install cec-utils`.
2. Copy `cec-input.service` to `/etc/systemd/system`.
3. Reload the daemon with `# systemctl daemon-reload`
4. Start the service with `# systemctl start cec-input`.
5. Run `# journalctl -fu cec-input`.
6. Press the keys on your remote and watch the output. Direction keys tend to work, along with OK, back, exit and the 4 coloured buttons.
7. Assign your commands to keys in `/etc/systemd/system/cec-input.env`. The format is `key='command'` per line e.g.
`back='systemctl start getty@tty6'` will start `getty@tty6` when the key reported as `back` in the `journalctl` output is pressed.

8. Restart the service after adding new keys:
```
# systemctl daemon-reload
# systemctl restart cec-input
```

9. Enable the service to run on boot if it works as intended with `# systemctl enable cec-input`.

Note: stop the service if it conflicts with CEC input in other applications that offer their own CEC handler.
