FROM gentoo/stage3:latest

RUN emerge --sync || { echo 'Sync fallo'; exit 1; }

RUN emerge --update --deep --newuse @world || { echo 'fallo actulizacion'; exit 1; }

RUN emerge -v net-misc/telnet-bsd \
	neofetch \
	net-fs/samba \
	app-misc/mc \
	app-editors/vim \
	net-misc/curl || { echo 'fallo instlacion de paquetes'; exit 1; }

RUN useradd -m -s /bin/bash s-o && \
	echo 's-o:password' | chpasswd

# Para hacer las conexiones del samba y el telnet
EXPOSE 23 139 445

CMD ["/bin/bash"]
