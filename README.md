# AwardCoin
Shell script to install a [AwardCoin Masternode](http://www.awardcoin.org/) on a Linux server running Ubuntu 14.04, 16.04 or 18.04. Use it on your own risk.

***
## Installation:
```
git clone https://github.com/awardprj/awr-install
cd awr-install
bash awr-install.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the AwardCoin Coin Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **10000** **AwardCoin** to **MN1**.
4. Wait for 15 confirmations.
5. Go to **Tools -> "Debug console - Console"**
6. Type the following command: **masternode outputs**
7. Go to  ** Tools -> "Open Masternode Configuration File"
8. Add the following entry:
```
Alias Address Privkey TxHash Output_index
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* Output index:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
12. Open **Debug Console** in local wallet and type:
```
startmasternode "alias" "0" "MN1"
```
13. Open the Linux VPS console and type:
```
awardcoin-cli startmasternode local false
```
If successful, you will be answered:
Masternode successfully started
***

## Usage:
```
awardcoin-cli getinfo
awardcoin-cli mnsync status
awardcoin-cli masternode status
```
Also, if you want to check/start/stop **AwardCoin** , run one of the following commands as **root**:

**Ubuntu 16.04 or 18.04**:
```
systemctl status AwardCoin #To check the service is running.
systemctl start AwardCoin #To start AwardCoin service.
systemctl stop AwardCoin #To stop AwardCoin service.
systemctl is-enabled AwardCoin #To check whetether AwardCoin service is enabled on boot or not.
```
**Ubuntu 14.04**:  
```
/etc/init.d/AwardCoin start #To start AwardCoin service
/etc/init.d/AwardCoin stop #To stop AwardCoin service
/etc/init.d/AwardCoin restart #To restart AwardCoin service
```
***
