# Rocky Linux 9 image
FROM rockylinux:9

# Install OpenSSh server and vim
RUN dnf -y install openssh-server openssh-clients vim
RUN dnf -y install python3.11
# Uncomment this line if you need devel tools
# RUN dnf -y groupinstall development

# Created public key. It's required when starting sshd
RUN ssh-keygen -f /etc/ssh/ssh_host_rsa_key -N '' -t rsa
RUN ssh-keygen -f /etc/ssh/ssh_host_ecdsa_key -N '' -t ecdsa

# Allow login as root
RUN sed -ri 's/^#PermitEmptyPasswords no/PermitEmptyPasswords yes/' /etc/ssh/sshd_config

# Specify root password
RUN echo "root:" | chpasswd

EXPOSE 22

# Create ansible user with password "ansible" and add to sudo group
RUN useradd -m ansible && echo "ansible:ansible" | chpasswd && usermod -aG wheel ansible

# Allow the sudo group to execute commands with root privileges without password
RUN echo '%wheel ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

# Definisci l'alias ll come un comando RUN che esegue ls -l
RUN echo "alias ll='ls -l'" >> ~/.bashrc
# Start sshd
CMD ["/usr/sbin/sshd", "-D"]
