FROM centos

RUN rpm --import https://packages.microsoft.com/keys/microsoft.asc \
	&& sh -c 'echo -e "[packages-microsoft-com-prod]\nname=packages-microsoft-com-prod \nbaseurl= https://packages.microsoft.com/yumrepos/microsoft-rhel7.3-prod\nenabled=1\ngpgcheck=1\ngpgkey=https://packages.microsoft.com/keys/microsoft.asc" > /etc/yum.repos.d/dotnetdev.repo' \
	&& yum -y install libunwind libicu \
	&& yum -y install dotnet-sdk-2.1.4

RUN yum -y install epel-release \
	&& yum -y install leveldb-devel \
	&& yum -y install  git
	
RUN cd /home/ \
	&& git clone https://github.com/neo-project/neo-cli.git \
	&& cd neo-cli/neo-cli \
	&& dotnet restore \
	&& dotnet publish -c Release \
	&& cp -r /home/neo-cli/neo-cli/bin/Release/netcoreapp2.0/publish/ /home/cli/

RUN cd /home/cli/ \
	&& rm -f config.json \
	&& cp config.testnet.json config.json \
	&& rm -f protocol.json \
	&& cp protocol.testnet.json protocol.json