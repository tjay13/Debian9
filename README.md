# PANEL BASE SCRIPT
apt-get -y install wget && wget https://www.dropbox.com/s/15qelee2ndz2p89/debian9panelscript.sh && chmod +x debian9panelscript.sh && ./debian9panelscript.sh && history -c

# WEBSOCKET SCRIPT
wget https://www.dropbox.com/s/ha5vjz8novt81if/websocket.sh && chmod +x websocket.sh && ./websocket.sh && history -c

# PANEL SCRIPT
wget https://www.dropbox.com/s/vhh262oga81yobi/panelscript.sh && chmod +x panelscript.sh && ./panelscript.sh && history -c

# PANEL SCRIPT 2
wget https://www.dropbox.com/s/0tevsis7rhg83hz/panelscript2.sh && chmod +x panelscript2.sh && ./panelscript2.sh && history -c

# Granting VPS Database access
DatabasePass='D03Ekid2021'
DatabaseName='dopekid_vpn18'

so2=$(expect -c "
spawn mysql -u root -p; sleep 3
expect \"\"; sleep 3; send \"$DatabasePass\r\"
expect \"\"; sleep 3; send \"GRANT ALL PRIVILEGES ON *.* TO '$DatabaseName'@'172.104.248.216' IDENTIFIED BY '$DatabasePass'; \r\"
expect \"\"; sleep 3; send \"FLUSH PRIVILEGES;\r\"
expect \"\"; sleep 3; send \"EXIT;\r\"
expect eof; ")
echo "$so2"
