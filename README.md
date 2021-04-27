# Referência cruzada dos comandos dos gerenciadores de pacotes

Uma comparação dentre os principais comandos para gerenciar os pacotes pelo prompt do shell nas diversas distribuições Linux.

:eyes: As células em branco não necessariamente indicam que o referido comando não exista, pois apenas pode estar desconhecido pelo autor.

## Comandos

|  | dpkg | rpm | apt | dnf | yum |
| --: | :-: | :-: | :-: | :-: | :-: |
| Significado | Debian Package | RPM Package Manager | Advanced Packaging Tool | Dandified Yum | Yellow dog Updater, Modified |
| Extensão do arquivo | *.deb | *.rpm | *.deb | *.rpm | *.rpm |
| Distros que adotam o empacotamento | Debian, Ubuntu, Linux Mint, Knoppix | Red Hat, Fedora, Suse, CentOS, Mandriva, Yellow Dog, Linpus | Debian, Ubuntu, Linux Mint, Knoppix | CentOS, RHEL, Fedora | Red Hat, Fedora, Suse, CentOS, Mandriva, Yellow Dog, Linpus |
| Configuração dos repositórios |  |  | /etc/apt/sources.list | /etc/dnf/dnf.conf e /etc/yum.repos.d/ | /etc/yum.conf ou /etc/yum.repos.d/ |


| Tarefa | Comando |  |  |  |  |
| :-- | :-- | :-- | :-- | :-- | :-- |
| Instalar pacote do local | dpkg -i \<pacote> | rpm -i \<pacote> |  | dnf install \<pacote> | yum localinstall \<pacote> |
| Atualizar pacote do local |  | rpm -U \<pacote> |  | dnf upgrade \<pacote> | yum localupdate \<pacote> |
| Atualizar pacote do repo |  |  |  | dnf upgrade \<pacote> | yum update \<pacote> |
| Atualizar pacote se estiver instalado |  | rpm -F \<pacote> |  |  |  |
| Instalar pacote do repo |  |  | apt-get install \<pacote> | dnf install \<pacote> | yum install \<pacote> |
| Instalar grupo de pacotes |  |  |  | dnf group install \<grupo> | yum groupinstall \<grupo> |
| Reinstalar um pacote |  |  |  | dnf reinstall \<pacote> | yum reinstall \<pacote> |
| Atualizar grupo de pacotes |  |  |  | dnf group upgrade \<grupo> | yum groupupdate \<grupo> |
| Remover pacote | dpkg -r \<pacote> | rpm -e \<pacote> | apt-get remove \<pacote> | dnf remove \<pacote> | yum remove \<pacote> |
| Remover pacotes órfãos |  |  |  |  | package-cleanup --orphans |
| Remover pacotes solitários |  |  |  |  | package-cleanup --leaves |
| Remover grupo de pacotes |  |  |  | dnf group remove \<grupo> | yum groupremove \<grupo> |
| Listar arquivos do pacote instalado | dpkg -L \<pacote> | rpm -ql \<pacote> |  | dnf repoquery --list \<pacote> |  |
| Listar arquivos do pacote não instalado | dpkg-deb -c \<pacote> | rpm -qpl \<pacote> |  | dnf repoquery --list \<pacote> |  |
| Mostrar informações do pacote instalado | dpkg -s \<pacote> | rpm -qi \<pacote> | apt-cache show \<pacote> | dnf info \<pacote> | yum info \<pacote> |
| Mostrar informações do pacote não instalado |  | rpm -qpi \<pacote> | apt-cache show \<pacote> | dnf info \<pacote> | yum info \<pacote> |
| Mostrar novidades da versão do pacote |  | rpm -q --changelog \<pacote> | apt-listchanges \<pacote> |  |  |
| Display overview of how many groups are installed and available |  |  |  | dnf group \<grupo> |  |
| Mostrar detalhes sobre um grupo de pacotes |  |  |  | dnf group info \<grupo> | yum groupinfo \<grupo> |
| Extrair arquivo do pacote | dpkg-deb -–extract \<pacote> | rpm2cpio \<pacote>|cpio -vid |  |  |  |
| Listar todos os pacotes instalados | dpkg -l | rpm -qa |  | dnf list --installed | yum list installed |
| Listar todos os pacotes disponíveis | N/A | N/A | apt-cache pkgnames | dnf list | yum list |
| Listar os grupos de pacotes disponíveis |  |  |  | dnf group list \<grupo> | yum grouplist |
| Verificar integridade do pacote |  | rpm -K \<pacote> |  |  |  |
| Verificar integridade dos arquivos instalados do pacote |  | rpm -V \<pacote> |  |  |  |
| Verificar integridade dos arquivos instalados de todos os pacotes | debsums | rpm -Va |  |  |  |
| Mostrar qual pacote pertence o arquivo | dpkg -S \<arquivo> | rpm -qf \<arquivo> | apt-file search \<arquivo> | dnf provides \<arquivo> | yum provides \<arquivo> |
| Listar todos os arquivos que acompanham o arquivo no pacote |  | rpm -qdf \<arquivo> |  |  |  |
| Mostrar as dependências do pacote |  | rpm -qpR \<pacote> | apt-cache depends \<pacote> | dnf repoquery --deplist \<pacote> | yum deplist \<pacote> |
| Mostrar os pacotes que dependem do pacote |  | rpm -q --whatrequires \<pct> | apt-cache rdepends \<pacote> |  | yum resolvedep \<dependência> |
| Procurar expressão em pacotes do repositório |  |  | apt-cache search \<expressão> | dnf search \<expressão> | yum search \<expressão> |
| Procurar pacotes nos repositórios |  |  |  | dnf search \<pacote> | yum search \<pacote> |
| Exibir os repositórios de software configurados |  |  |  | dnf repolist --all | yum repolist |
| Atualizar lista de pacotes dos repositórios |  |  | apt-get update |  | (o yum faz automaticamente a cada uso) |
| Verificar novas atualizações |  |  | apt-get -s upgrade | dnf check-update | yum check-update |
| Atualizar pacotes |  |  | apt-get upgrade | dnf upgrade | yum update |
| Atualizar todo o sistema |  |  | apt-get dist-upgrade | dnf system-upgrade download --releasever=30 | yum upgrade |
| Remover pacote do cache local |  |  | apt-get clean | dnf clean packages | yum clean packages |
| Removes cache files generated from the repository metadata |  |  |  | dnf clean dbcache |  |
| Marks the repository metadata expired |  |  |  | dnf clean expire-cache |  |
| Removes repository metadata |  |  |  | dnf clean metadata |  |
| Remover somente pacotes obsoletos do cache local |  |  | apt-get autoclean |  |  |
| Remover cabeçalhos do cache local |  |  | apt-file purge |  | yum clean headers |
| Remover cabeçalhos obsoletos do cache local |  |  |  |  | yum clean oldheaders |
| Remover pacotes e cabeçalhos do cache local |  |  |  | dnf clean all | yum clean all |
| Mostrar estado do cache |  |  | apt-cache stats |  |  |

## Referências

- ABREU, A. *All you have to know about RPM.* FedoraNEWS.ORG. March 09, 2004. Disponível em: <https://fedoranews.org/alex/tutorial/rpm/>

- AOKI, O. *Referência Debian.* Versão 2.77, 10 de Janeiro de 2021. Disponível em: <https://www.debian.org/doc/manuals/debian-reference/>

- BAILEY, E. C.; NASRAT, P.; SAOU, M.; SKYTTÄ, V. *Maximum RPM: Taking the RPM Package Manager to the Limit.* Red Hat, Inc., 2000. Disponível em: <http://ftp.rpm.org/max-rpm/>

- BAYDAN, İ. *Apt and Apt-Get Tutorial With Examples.* POFTUT. December 19, 2016. Disponível em: <https://www.poftut.com/apt-and-apt-get-tutorial-with-examples/>

- CHINTHAGUNTLA, K. *Linux package management with YUM and RPM.* Enable Sysadmin, A Red Hat community publication for sysadmins. April 22, 2020. Disponível em: <https://www.redhat.com/sysadmin/how-manage-packages>

- *DNF Command Reference.* DNF, the next-generation replacement for YUM, 2021. Disponível em: <https://dnf.readthedocs.io/en/latest/command_ref.html>

- EDGEWALL SOFTWARE *Basic Yum Commands and how to use them.* Trac Open Source Project. Disponível em: <http://yum.baseurl.org/wiki/YumCommands.html>

- RED HAT, INC. *System Administrator's Guide.* Fedora 33 User Documentation, April 27, 2021. Disponível em: <https://docs.fedoraproject.org/en-US/fedora/f33/system-administrators-guide/>

- PRAKASH, A. *Using apt Commands in Linux [Complete Guide].* It's FOSS, chmod777 Media Tech. September 18, 2020. Disponível em: <https://itsfoss.com/apt-command-guide/>

- *RPM Documentation.* Disponível em: <https://rpm.org/documentation.html>

- SILVA, G. N. *Como usar o APT.* Debian Documentação HOWTOs. Versão 1.8.11, Agosto de 2005. Disponível em: <https://www.debian.org/doc/manuals/apt-howto/>

- *Using the DNF software package manager.* Fedora Docs, April 27, 2021. Disponível em: <https://docs.fedoraproject.org/en-US/quick-docs/dnf/>

## Licença

[MIT](./LICENSE)
