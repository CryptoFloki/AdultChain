# AdultChain 
Shell script to install a [AdultChain Masternode](https://adultchain.xxx/) on a Linux server running Ubuntu 16.04. This is a light modification of Zoldur's original script. Use it on your own risk.
***

## VPS installation
```
wget -q https://raw.githubusercontent.com/zoldur/AdultChain/master/adultchain_install.sh
bash adultchain_install.sh
```
* Press Enter when asked for Genkey.
```
systemctl stop AdultChain

nano /root/.adultchain/adultchain.conf
```
* Copy paste these to sync your VPS.(If any nodes already, delete them and replace with thesse): 
```
addnode=80.240.19.104:6969
addnode=104.238.188.180:6969
addnode=149.28.132.28:6969
addnode=62.210.178.69:6969
addnode=159.65.33.119:6969
addnode=149.28.51.169:6969
```
* SAVE CTRL+X then ENTER
```
adultchaind -reindex
```
* It will then appear to freeze. Close it and open it again.
* Check blocks is synching with
```
adultchain-cli getinfo
```
* When blocks matches your wallet use this command until requests have 999 near the buttom.
```
adultchain-cli mnsync status


```
***

## Desktop wallet setup  

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps:  
1. Open the AdultChain Desktop Wallet.  
2. Go to RECEIVE and create a New Address: **MN1**  
3. Send **20000** XXX **MN1**. You need to send all 20000 coins in one single transaction.
4. Wait for 15 confirmations.
5. Go to **Help -> "Debug Window - Console"**  
6. Type the following command: **masternode outputs**  
7. Go to  **Tools -> "Open Masternode Configuration File"**
8. Add the following entry:
```
Alias Address Privkey TxHash TxIndex
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* TxIndex:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is un
12. Open **Debug Console** and type:
```
startmasternode alias false MNNAME
``` 
14. Login to your VPS and check your masternode status by running the following command:.
```
adultchain-cli masternode status
```
If status 4, your MN is now running and you can close the VPS.
***

## Usage:
```
adultchain-cli masternode status  
adultchain-cli getinfo
```
Also, if you want to check/start/stop **AdultChain**, run one of the following commands as **root**:

```
systemctl status AdultChain #To check if AdultChain service is running  
systemctl start AdultChain #To start AdultChain service  
systemctl stop AdultChain #To stop AdultChain service  
systemctl is-enabled AdultChain #To check if AdultChain service is enabled on boot  
```  
***

## Donations

Any donation is highly appreciated.

Zoldur:

**XXX**: F1ieS1U6UeihUfFpNjHL8VJnHPzwoj  
**BTC**: 3MQLEcHXVvxpmwbB811qiC1c6g21ZKa7Jh  
**ETH**: 0x26B9dDa0616FE0759273D651e77Fe7dd7751E01E  
**LTC**: LNZpK4rCd1JVSB3rGKTAnTkudV9So9zexB  

Floki:

**XXX**: XSoT8Lnp8vhTaHjHGcTGNoDDTA5Tm2nDz9
**BTC**: 1C7cp7WK9hpxDSVMDnyiDXXfM2NyGFqxLe
