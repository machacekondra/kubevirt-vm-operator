FROM quay.io/operator-framework/ansible-operator:v0.8.1

COPY watches.yaml ${HOME}/watches.yaml

COPY fedora29.yaml ${HOME}/fedora29.yaml

# TODO: remove when ansible-oprator has Ansible 2.8
USER root
RUN pip install -U ansible
USER 1001
