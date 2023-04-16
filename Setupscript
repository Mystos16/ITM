sudo apt-get update
sudo apt-get install -y apt-transport-https
sudo apt-get update
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
rm packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install -y dotnet-sdk-6.0
sudo apt-get install -y aspnetcore-runtime-6.0

# install sql server
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo tee /etc/apt/trusted.gpg.d/microsoft.asc
sudo add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/20.04/mssql-server-2022.list)"
sudo apt-get update
sudo apt-get install -y mssql-server
sudo /opt/mssql/bin/mssql-conf setup
systemctl status mssql-server --no-pager

# install git en install backend
sudo apt-get install -y git
cd -
git clone https://github.com/microsoft/Bing-Maps-Fleet-Tracker

dotnet build Backend/src/Trackable.Web/
dotnet run --project Backend/src/Trackable.Web/Trackable.Web.csproj
