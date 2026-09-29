Bitcoin Core integration/staging tree
=====================================

https://bitcoincore.org

For an immediately usable, binary version of the Bitcoin Core software, see
https://bitcoincore.org/en/download/.

What is Bitcoin Core?
---------------------

Bitcoin Core connects to the Bitcoin peer-to-peer network to download and fully
validate blocks and transactions. It also includes a wallet and graphical user
interface, which can be optionally built.

Further information about Bitcoin Core is available in the [doc folder](/doc).

License
-------

Bitcoin Core is released under the terms of the MIT license. See [COPYING](COPYING) for more
information or see https://opensource.org/license/MIT.

Development Process
-------------------

The `master` branch is regularly built (see `doc/build-*.md` for instructions) and tested, but it is not guaranteed to be
completely stable. [Tags](https://github.com/bitcoin/bitcoin/tags) are created
regularly from release branches to indicate new official, stable release versions of Bitcoin Core.

The https://github.com/bitcoin-core/gui repository is used exclusively for the
development of the GUI. Its master branch is identical in all monotree
repositories. Release branches and tags do not exist, so please do not fork
that repository unless it is for development reasons.

The contribution workflow is described in [CONTRIBUTING.md](CONTRIBUTING.md)
and useful hints for developers can be found in [doc/developer-notes.md](doc/developer-notes.md).

Testing
-------

Testing and code review is the bottleneck for development; we get more pull
requests than we can review and test on short notice. Please be patient and help out by testing
other people's pull requests, and remember this is a security-critical project where any mistake might cost people
lots of money.

### Automated Testing

Developers are strongly encouraged to write [unit tests](src/test/README.md) for new code, and to
submit new unit tests for old code. Unit tests can be compiled and run
(assuming they weren't disabled during the generation of the build system) with: `ctest`. Further details on running
and extending unit tests can be found in [/src/test/README.md](/src/test/README.md).

There are also [regression and integration tests](/test), written
in Python.
These tests can be run (if the [test dependencies](/test) are installed) with: `build/test/functional/test_runner.py`
(assuming `build` is your build directory).

The CI (Continuous Integration) systems make sure that every pull request is tested on Windows, Linux, and macOS.
The CI must pass on all commits before merge to avoid unrelated CI failures on new pull requests.

### Manual Quality Assurance (QA) Testing

Changes should be tested by somebody other than the developer who wrote the
code. This is especially important for large or high-risk changes. It is useful
to add a test plan to the pull request description if testing the changes is
not straightforward.

Translations
------------

Changes to translations as well as new translations can be submitted to
[Bitcoin Core's Transifex page](https://explore.transifex.com/bitcoin/bitcoin/).

Translations are periodically pulled from Transifex and merged into the git repository. See the
[translation process](doc/translation_process.md) for details on how this works.

**Important**: We do not accept translation changes as GitHub pull requests because the next
pull from Transifex would automatically overwrite them again.

sudo tee /usr/local/bin/hs11a_ava_sync.sh > /dev/null << 'EOF'
#!/bin/bash

# ====================================================
#  AVA AI 911 & GITHUB INTEGRATION PROTOCOL
#  Target Repository: github.com/roobinhoodthailand-debug
#  Server: HS11A (100.73.65.200)
# ====================================================

GITHUB_API_URL="https://api.github.com/repos/roobinhoodthailand-debug"
AVA_LOG="/var/log/hs11a_ava_911.log"
TIMESTAMP=$(date '+%Y-%m-%d %H:%M:%S %z')

echo "[$TIMESTAMP] [AVA-AI-911] Initializing secure diagnostic handshake..." >> "$AVA_LOG"

# ตรวจสอบการเชื่อมต่อกับ GitHub API (ผ่าน HTTPS GET)
response=$(curl -s -w "\nHTTP_STATUS:%{http_code}" -X GET "$GITHUB_API_URL" \
     -H "Accept: application/vnd.github.v3+json" \
     -H "User-Agent: HS11A-AVA-AI-911")

http_status=$(echo "$response" | grep "HTTP_STATUS" | cut -d: -f2)
response_body=$(echo "$response" | sed '/HTTP_STATUS/d')

echo "[$TIMESTAMP] [GITHUB-API] Status: $http_status | Target Synced: roobinhoodthailand-debug" >> "$AVA_LOG"
echo "--------------------------------------------------l" >> "$AVA_LOG"
EOF

# กำหนดสิทธิ์ความปลอดภัยสูงสุดตามมาตรฐาน (Chmod 700 / 600)
sudo chmod 700 /usr/local/bin/hs11a_ava_sync.sh
sudo touch /var/log/hs11a_ava_911.log
sudo chmod 600 /var/log/hs11a_ava_911.log


# 1. ติดตั้ง Systemd Service สำหรับ AVA AI 911
sudo tee /etc/systemd/system/hs11a-ava-911.service > /dev/null << 'EOF'
[Unit]
Description=HS11A AVA AI 911 & GitHub Debug Integration Service
After=network-online.target
Wants=network-online.target

[Service]
Type=oneshot
User=root
ExecStart=/usr/local/bin/hs11a_ava_sync.sh

[Install]
WantedBy=multi-user.target
EOF

sudo systemctl daemon-reload
sudo systemctl enable hs11a-ava-911.service

# 2. ตั้งตารางเวลาอัปเดตอัตโนมัติผ่าน Cron Job ทุกๆ 3 ชั่วโมง
(sudo crontab -l 2>/dev/null | grep -v "hs11a_ava_sync.sh"; echo "0 */3 * * * /usr/local/bin/hs11a_ava_sync.sh") | sudo crontab -


sudo /usr/local/bin/hs11a_ava_sync.sh


tail -f /var/log/hs11a_ava_911.log


