FROM rockylinux:9
ENV ANSIBLE_HOST_KEY_CHECKING False
RUN dnf install epel-release -y && \
    dnf update -y && \
    dnf install -y openssh-server openssh-clients net-tools vim && \
    dnf install -y ansible

# Definisci l'alias ll come un comando RUN che esegue ls -l
RUN echo "alias ll='ls -l --color=auto'" >> ~/.bashrc
# Impostare i colori per la shell bash
RUN echo "export PS1='\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '" >> ~/.bashrc
CMD /bin/bash
