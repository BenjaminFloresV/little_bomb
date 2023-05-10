FROM ubuntu:20.04

# This tells to package manager (apt-get) to install
# packages with no user interaction on the prompt
ARG DEBIAN_FRONTEND=noninteractive

# - apt-get clean: This command clears the local repository of retrieved packages files.
#                  This helps to reduce the size of the Docker image and can also help to
#                  ensure that the latest package are downloaded during the next update.
#
# - apt-get -y update: This command updates the package list for the APT package manager.
#                      It retrieves the latest package information from the repositories specified
#                      in the sources.list file
#
# - apt-get install -y locales apt-utils: This command installs the 'locales' and 'apt-utils' packages using the
#                                         APT package manager. The 'locales' package provides support for 
#                                         (I18n) internationalization and localization (I10n), while 'apt-utils' provices
#                                          a set of utilities that can be used to manage packages.
# - locale-gen en_US.UTF-8: This command generates a UTF-8 locale for the 'en_US' locale, which is commonly used
#                           in many Linux distributions. This sets the default locale to be used in the container
#                           to 'en_US.UTF-8'    
RUN apt-get clean && apt-get -y update && apt-get install -y locales apt-utils && locale-gen en_US.UTF-8



#   This environment variable sets the default language used in the container to US English 
# with the UTF-8 character encoding.
ENV LANGUAGE=en_US.UTF-8
# This environment variable sets the value of the LC_ALL locale variable to US English with the UTF-8 character 
# encoding. This variable overrides all other locale-related environment variables and is used to set the default 
# locale for all system components.
ENV LC_ALL=en_US.UTF-8
# Sets the value of the LC_CTYPE locale variable to UTF-8. This variable specifies the character classification and enconding rules
# for the current locale.
ENV LC_CTYPE=UTF-8
# Sets the value of LANG locale variable to US English with UTF-8 character enncoding. This variable specifies the default language
# and character encoding used by the system when no other locale-related environment variables are set.
ENV LANG=en_US.UTF-8
# This environment variable sets the terminal type to 'xterm', which is a widely used terminal emulation software
# This is often used to ensure that the terminal emulator behaves correctly when running interactive commands in the 
# container
ENV TERM=xterm


# apt-get dist-upgrade -y --force-yes: Upgrades the packages to their latest versions and may also remove obsolete
# packages or install new ones to satisfy dependencies. The '-y' option answers yes to all prompts, and the --force-yes
# option forces the installation of packages even if it requires additional dependencies or removal of conflicting packages.
# apt-get install -y software-properties-commmon: this command installs all the software-properties-common package which provides a set of
# utilities for adding and managing software repositories. It is often used to add additional repositories to the package
# manager's sources list
RUN apt-get dist-upgrade -y --force-yes && apt-get install -y software-properties-common
# add-apt-repository -y ppa:git-core/ppa: This command adds the Personal Package Archive (PPA) for Git 
# to the list of software repositories used by the APT manager. The -y option answers "yes" to any prompts
# during the addition of the repository
# apt-get update: Updates the package list for the APT package manager. It retrieves the latest package information from the
# repositories specified in the source.list file, inclduing the newly added Git PPA repository.
RUN add-apt-repository -y ppa:git-core/ppa && apt-get update
#
RUN add-apt-repository -y ppa:inkscape.dev/stable && apt-get update

# The RUN apt-get install -y --force-yes \ less \ unzip \ vim \ git \ python3 \ python3-dev \ python3-setuptools \ python3-pip \ virtualenv \ && apt-get clean command in a Dockerfile installs multiple packages in a single RUN instruction.
# apt-get install -y --force-yes: This command installs the specified packages and their dependencies. The -y option answers yes to all prompts, and the --force-yes option forces the installation of packages even if it requires additional dependencies or removal of conflicting packages.
# less: This package provides a pager program for viewing text files in the terminal.
# unzip: This package provides a utility for extracting files from ZIP archives.
# vim: This package provides a text editor with advanced features for editing code and other text files.
# git: This package provides a version control system for tracking changes in source code during software development.
# python3: This package provides the Python 3 programming language runtime.
# python3-dev: This package provides header files and static libraries for developing Python 3 extensions.
# python3-setuptools: This package provides utilities for installing Python packages and managing dependencies.
# python3-pip: This package provides a tool for installing and managing Python packages.
# virtualenv: This package provides a tool for creating isolated Python environments.
# apt-get clean: This command clears the local repository of retrieved package files. This helps to reduce the size of the Docker image and can also help to ensure that the latest packages are downloaded during the next update.
RUN apt-get install -y --force-yes \
    less \
    unzip \
    vim \
    git \
    python3 \
    python3-dev \
    python3-setuptools \
    python3-pip \
    virtualenv \
    && apt-get clean


RUN apt-get install -y --force-yes \
    sqlite3 \
    mysql-client \
    postgresql-client \
    libmysqlclient-dev \
    libpq-dev \
    && apt-get clean


#The RUN apt-get install -y --force-yes \ gcc \ libssl-dev \ libgeoip1 \ libldap2-dev \ libsasl2-dev \ libaio1 \ libaio-dev \ libxml2-dev \ libxmlsec1-dev \ pkg-config \ && apt-get clean command in a Dockerfile installs multiple packages in a single RUN instruction.

# Here's what each command does:
# apt-get install -y --force-yes: This command installs the specified packages and their dependencies. The -y option answers yes to all prompts, and the --force-yes option forces the installation of packages even if it requires additional dependencies or removal of conflicting packages.
# gcc: This package provides the GNU Compiler Collection, which is a set of compilers for various programming languages.
# libssl-dev: This package provides development files for the OpenSSL cryptographic library, which is commonly used in secure network communication.
# libgeoip1: This package provides the GeoIP library for geographic location lookup based on IP addresses.
# libldap2-dev: This package provides development files for the LDAP (Lightweight Directory Access Protocl) library.
# libsasl2-dev: This package provides development files for the SASL (Simple Authentication and Security Layer) library, which provides authentication mechanisms for network protocols.
# libaio1: This package provides the asynchronous I/O library for Linux.
# libaio-dev: This package provides development files for the asynchronous I/O library.
# libxml2-dev: This package provides development files for the XML parsing and validation library.
# libxmlsec1-dev: This package provides development files for the XML security library, which provides support for XML digital signatures and encryption.
# pkg-config: This package provides a tool for retrieving information about installed libraries and their dependencies.
# apt-get clean: This command clears the local repository of retrieved package files. This helps to reduce the size of the Docker image and can also help to ensure that the latest packages are downloaded during the next update.

# The purpose of these commands is to install a set of packages and development files that are often needed for building and running 
# software applications that require support for network communication, security, and I/O operations. The use of the --force-yes option should be used with caution as it may potentially cause issues with package dependencies or conflicts. The apt-get clean command is used to reduce the size of the Docker image by removing cached package files after the installation process is completed.
RUN apt-get install -y --force-yes \
    gcc \
    libssl-dev \
    libgeoip1 \
    libldap2-dev \
    libsasl2-dev	\
    libaio1 \
    libaio-dev \
    libxml2-dev \
    libxmlsec1-dev \
    pkg-config \
    && apt-get clean


# Here's what each command does:
# apt-get install -y --force-yes: This command installs the specified packages and their dependencies. The -y option answers yes to all prompts, and the --force-yes option forces the installation of packages even if it requires additional dependencies or removal of conflicting packages.
# graphviz: This package provides a set of tools for generating graph and network diagrams.
# imagemagick: This package provides a set of tools for manipulating and converting images.
# apt-get clean: This command clears the local repository of retrieved package files. This helps to reduce the size of the Docker image and can also help to ensure that the latest packages are downloaded during the next update.
# The purpose of these commands is to install the graphviz and imagemagick packages, which are commonly used in software applications 
# that require support for graph and image manipulation. The use of the --force-yes option should be used with caution as it may potentially cause issues with package dependencies or conflicts. The apt-get clean command is used to reduce the size of the Docker image by removing cached package files after the installation process is completed.
RUN apt-get install -y --force-yes \
    graphviz \
    imagemagick \
    && apt-get clean


# Here's what each command does:
# echo "postfix postfix/main_mailer_type string 'Internet Site'\npostfix postfix/mailname string mail.example.com" | debconf-set-selections: This command sets the default values for the Postfix package using the debconf-set-selections utility. Specifically, it sets the mailer type to "Internet Site" and the mail name to "mail.example.com". This is useful for automatically setting up the Postfix package during installation without user interaction.
# apt-get install -y postfix: This command installs the Postfix mail server package and its dependencies. Postfix is a popular mail transfer agent (MTA) that is commonly used for sending and receiving emails.
# apt-get clean: This command clears the local repository of retrieved package files. This helps to reduce the size of the Docker image and can also help to ensure that the latest packages are downloaded during the next update.

# The purpose of these commands is to install and configure the Postfix mail server package with default values. The echo command sets the default values for Postfix during installation and the apt-get install command installs the package and its dependencies. The apt-get clean command is used to reduce
# the size of the Docker image by removing cached package files after the installation process is completed
RUN \
    echo "postfix postfix/main_mailer_type string 'Internet Site'\npostfix postfix/mailname string mail.example.com" | debconf-set-selections \
    && apt-get install -y postfix \
    && apt-get clean

# Here's what each command does:
# cp -f /etc/services /var/spool/postfix/etc/: This command copies the /etc/services file, which contains a list of network services and their port numbers, from the host system to the /var/spool/postfix/etc/ directory inside the container. This is necessary for Postfix to map port numbers to service names.
# cp -f /etc/resolv.conf /var/spool/postfix/etc/: This command copies the /etc/resolv.conf file, which contains the system's DNS resolver configuration, from the host system to the /var/spool/postfix/etc/ directory inside the container. This is necessary for Postfix to be able to resolve domain names for outgoing email delivery.

# The purpose of these commands is to copy the necessary configuration files from the host system to the Postfix mail server's configuration directory inside the container. This ensures that Postfix is able to function properly and communicate with other systems on the network. The use of the -f option with cp forces the overwrite
# of the files if they already exist in the destination directory.
RUN cp -f /etc/services /var/spool/postfix/etc/
RUN cp -f /etc/resolv.conf /var/spool/postfix/etc/


# Here's what each command does:
# apt-get install -y: This command installs the specified packages and their dependencies. The -y option answers yes to all prompts.
# rsyslog: This package provides a system logging daemon that enables system administrators to collect, manage, and store log messages from various sources.
# supervisor: This package provides a process control system that enables system administrators to manage and monitor multiple processes running on a system.
# nginx: This package provides a web server and reverse proxy server that is commonly used in web application development and deployment.
# curl: This package provides a command-line tool for transferring data from or to a server using various protocols, such as HTTP, FTP, and LDAP.
# gettext: This package provides a set of tools for translating messages in software applications into different languages.
# apt-get clean: This command clears the local repository of retrieved package files. This helps to reduce the size of the Docker image and can also help to ensure that the latest packages are downloaded during the next update.
# The purpose of these commands is to install several packages that are commonly used in web application development and deployment. rsyslog and supervisor
# provide system logging and process management capabilities, respectively. nginx provides a web server and reverse proxy server that is commonly used to serve static content and proxy requests to application servers. curl provides a convenient command-line tool for testing web applications and APIs. gettext provides tools for localization and internationalization of software applications. The apt-get clean command is used to reduce the size of the Docker image by removing cached package files after the installation process is completed.
RUN apt-get install -y \
    rsyslog \
    supervisor \
    nginx \
    curl \
    gettext \
    && apt-get clean


# Here's what the command does:

# rm -rf /var/lib/apt/lists/*: This command removes all files and directories in the /var/lib/apt/lists/ directory. This directory contains the lists of available packages in the local repository cache, which are used by apt-get during package installation and updates.
# The purpose of this command is to reduce the size of the Docker image by removing unnecessary files and directories that are not needed after package installation. Since the package lists are automatically re-downloaded when apt-get update is executed, removing them has no impact on the functionality of the container.
RUN rm -rf /var/lib/apt/lists/*



# Here's what each command does:
# pip3 install uwsgi: This command installs the uwsgi package, which is a fast, self-healing and developer-friendly application server for Python web applications. uwsgi is often used as a WSGI server to run Python web applications in production environments.
# pip3 install uwsgitop: This command installs the uwsgitop package, which is a command-line utility for monitoring and profiling uwsgi servers. uwsgitop provides real-time statistics and performance metrics for uwsgi server processes.

# The purpose of these commands is to install the uwsgi and uwsgitop packages, which are commonly used in Python web application development and deployment. uwsgi provides a fast and reliable application server for running Python web applications in production environments, while uwsgitop provides useful tools for monitoring and profiling uwsgi servers. These packages can be used together to optimize the performance and stability of Python web applications.
RUN pip3 install uwsgi

RUN pip3 install uwsgitop

# The ARG USERHOST_UID=1000 and ARG USERHOST_GID=1000 commands in a Dockerfile define two build arguments with default values of 1000.
# The RUN groupadd --non-unique --gid $USERHOST_GID django command creates a new system group called django with the GID (group ID) value equal to the $USERHOST_GID argument. The --non-unique option allows for the creation of groups with the same GID value as an existing group, which may be useful in certain situations.
# The RUN getent group $USERHOST_GID && useradd -u $USERHOST_UID --gid $USERHOST_GID -s /bin/bash -m django command checks if a group with the GID value specified in the $USERHOST_GID argument exists using the getent command. If the group exists, the command proceeds to create a new system user called django with the UID (user ID) value equal to the $USERHOST_UID argument, and adds the user to the django group using the --gid option. The -s /bin/bash option specifies the user's default shell, and the -m option creates a home directory for the user.

# The purpose of these commands is to create a new system user and group with the specified UID and GID values. This can be useful for ensuring that the user running the Django application inside the container has the correct permissions and ownership of files and directories. By default, the UID and GID values of the django user and group are set to 1000, but they can be overridden during the build process using the --build-arg option.
ARG USERHOST_UID=1000
ARG USERHOST_GID=1000
RUN groupadd --non-unique --gid $USERHOST_GID django
RUN getent group $USERHOST_GID && useradd -u $USERHOST_UID --gid $USERHOST_GID -s /bin/bash -m django

RUN mkdir /srv/env
# Here's what the command does:

# /bin/chown: This is a command-line tool for changing the ownership of files and directories.

# django:: This specifies the user and group that the ownership should be changed to. The django user and group were created earlier in the Dockerfile using the useradd and groupadd commands.

# /srv/env: This is the path to the directory whose ownership is being changed.

# The purpose of this command is to ensure that the django user and group have the necessary permissions to access and modify the files and directories inside the /srv/env directory. By changing the ownership of the directory, the django user and group become the owners of the directory and can access it as needed. This is a common practice in Dockerfiles to ensure that the application is executed under a specific user or group with the correct permissions to access the necessary files and directories.
RUN /bin/chown django: /srv/env

USER django


# The RUN mkdir /home/django/.nvm command creates a new directory called .nvm in the home directory of the django user.

# The ENV NVM_DIR /home/django/.nvm command sets the NVM_DIR environment variable to /home/django/.nvm, which is the path to the .nvm directory created earlier.

# The RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.38.0/install.sh | bash && . ~/.nvm/nvm.sh && nvm install stable && nvm use stable && nvm alias stable && npm install -g gulp yarn command installs the Node Version Manager (NVM) and Node.js on the container. It also installs the gulp and yarn packages globally using npm.

# Here's what each command does:

# curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.38.0/install.sh | bash: This command downloads and runs the NVM installation script, which installs NVM on the container. NVM allows users to easily switch between different versions of Node.js.

# . ~/.nvm/nvm.sh: This command sources the NVM script, which sets up the NVM environment variables and functions.

# nvm install stable: This command installs the latest stable version of Node.js using NVM.

# nvm use stable: This command sets the stable version of Node.js as the default version to be used.

# nvm alias stable: This command creates an alias for the stable version of Node.js.

# npm install -g gulp yarn: This command installs the gulp and yarn packages globally using npm. gulp is a build tool for web applications, while yarn is a package manager for Node.js.

# The purpose of these commands is to set up a Node.js development environment for the django user. This is useful for building and deploying web applications that use Node.js and related tools. By installing NVM and Node.js, users can easily switch between different versions of Node.js and ensure that their applications are using the correct version. Installing gulp and yarn globally also makes it easy to manage dependencies and build tools for Node.js applications.
RUN mkdir /home/django/.nvm
ENV NVM_DIR /home/django/.nvm
RUN curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.38.0/install.sh | bash && \
    . ~/.nvm/nvm.sh && \
    nvm install stable && \
    nvm use stable && \
    nvm alias stable && \
    npm install -g gulp yarn


# Wouldn't execute when added to the RUN statement in the above block
# Source NVM when loading bash since ~/.profile isn't loaded on non-login shell

# The RUN echo "" >> ~/.bashrc && \ echo 'export NVM_DIR="$HOME/.nvm"' >> ~/.bashrc && \ echo '[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm' >> ~/.bashrc command modifies the .bashrc file for the django user by appending three lines to the end of the file. The three lines added to the .bashrc file set up the NVM environment variables and functions.

# Here's what each line does:

# echo "" >> ~/.bashrc: This command appends a blank line to the end of the .bashrc file.

# echo 'export NVM_DIR="$HOME/.nvm"' >> ~/.bashrc: This command appends a line to the end of the .bashrc file that sets the NVM_DIR environment variable to /home/django/.nvm.

# echo '[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh" # This loads nvm' >> ~/.bashrc: This command appends a line to the end of the .bashrc file that sources the NVM script and sets up the NVM environment variables and functions.

# The RUN echo "" >> ~/.bashrc && \ echo '[ -s "/srv/env/bin/activate" ] && . "/srv/env/bin/activate" # This loads django project environment' >> ~/.bashrc command modifies the .bashrc file for the django user by appending a line to the end of the file. This line sets up the environment for the Django project by sourcing the virtual environment script.

# Here's what the line does:

# echo "" >> ~/.bashrc: This command appends a blank line to the end of the .bashrc file.

# echo '[ -s "/srv/env/bin/activate" ] && . "/srv/env/bin/activate" # This loads django project environment' >> ~/.bashrc: This command appends a line to the end of the .bashrc file that sources the virtual environment script for the Django project. The virtual environment is located in the /srv/env/ directory and is activated using the activate script.

# The purpose of these commands is to set up the environment for the django user in the container. The NVM environment variables and functions are set up to ensure that the correct version of Node.js is used in the container. The virtual environment script for the Django project is sourced to ensure that the correct Python environment is used when running the Django project. These modifications to the .bashrc file are executed each time a new shell session is started, ensuring that the environment is set up correctly each time the container is started.
RUN echo "" >> ~/.bashrc && \
    echo 'export NVM_DIR="$HOME/.nvm"' >> ~/.bashrc && \
    echo '[ -s "$NVM_DIR/nvm.sh" ] && . "$NVM_DIR/nvm.sh"  # This loads nvm' >> ~/.bashrc

RUN echo "" >> ~/.bashrc && \
    echo '[ -s "/srv/env/bin/activate" ] && . "/srv/env/bin/activate"  # This loads django project environment' >> ~/.bashrc


# The RUN touch ~/.bash_history command in a Dockerfile creates an empty .bash_history file in the home directory of the django user.

# The .bash_history file is a text file that stores a history of commands that have been executed in the shell. By default, Bash, the default shell in many Unix-based systems, stores the last 500 commands in the .bash_history file.

# Creating an empty .bash_history file in the Docker image can be useful to avoid errors when the django user starts a new shell session inside the container. If the .bash_history file does not exist, Bash may display a warning message about the inability to read or write the history file. By creating an empty .bash_history file, this warning message can be avoided.

# The purpose of this command is to ensure that the .bash_history file exists for the django user in the Docker container, which can help avoid potential issues or error messages related to the shell history.
RUN touch ~/.bash_history


# The USER root command switches the user context to the root user for the subsequent commands in the Dockerfile.

# The RUN locale-gen es_CL.UTF-8 command generates the es_CL.UTF-8 locale, which is a Spanish locale for Chile. A locale is a set of parameters that defines the user's language, region, and cultural conventions, such as date and time formats. Generating a locale is necessary to ensure that the system can correctly display and format data for the specific locale.

# The RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* command removes unnecessary files and directories from the container, freeing up disk space. The apt-get clean command removes the cached package files that were downloaded during the apt-get installation process, while the rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* command removes temporary files and directories created during the Docker build process.

# The purpose of these commands is to prepare the Docker image for deployment by ensuring that the necessary locale is generated and unnecessary files and directories are removed. By generating the necessary locale and cleaning up unnecessary files and directories, the Docker image can be made smaller and more efficient, reducing the amount of storage and network resources required to deploy the image.
USER root

RUN locale-gen es_CL.UTF-8

RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*


# The RUN echo "daemon off;" >> /etc/nginx/nginx.conf command in a Dockerfile appends the line daemon off; to the end of the /etc/nginx/nginx.conf file.

# nginx is a popular web server and reverse proxy that is commonly used in Docker-based web application stacks. By default, nginx runs as a daemon in the background, which means that it detaches itself from the terminal and continues to run even after the user logs out.

# The daemon off; directive in the nginx.conf file tells nginx to run in the foreground, rather than as a background daemon. This is useful in the context of Docker containers, where the container should run a single process in the foreground. If nginx were to run as a daemon, the container would start and then immediately exit because the main process (nginx) would have detached from the container's main process and gone into the background.

# By adding the daemon off; directive to the nginx.conf file, nginx will run in the foreground and keep the container running as long as nginx is running. This allows the container to function as expected and serve web content over HTTP or HTTPS.
RUN echo "daemon off;" >> /etc/nginx/nginx.conf


# The COPY setup_django_project.sh /srv/ command in a Dockerfile copies the setup_django_project.sh file from the build context to the /srv/ directory inside the container.

# The RUN /bin/chmod +x /srv/setup_django_project.sh command sets the execute (+x) permission on the setup_django_project.sh script, which is located in the /srv/ directory. The chmod command allows the user to modify the file permissions of a file or directory.

# The purpose of these commands is to include a shell script in the Docker image that can be used to set up a Django project. By copying the setup_django_project.sh file into the container and setting the execute permission, the script can be run inside the container to install the necessary dependencies and set up the Django project. The script can be run manually or as part of a deployment process, depending on the specific use case.
COPY setup_django_project.sh /srv/
RUN /bin/chmod +x /srv/setup_django_project.sh

RUN touch /home/django/.bash_history

WORKDIR /srv/django

# The CMD ["supervisord", "-n"] command in a Dockerfile sets the default command to be executed when the container starts.

# supervisord is a process control system that is commonly used in Docker containers to manage multiple processes or services. The -n flag instructs supervisord to run in the foreground, which allows the Docker container to keep running while supervisord is active.

# By setting supervisord as the default command, the Docker container will start with supervisord running in the foreground, which will manage any additional processes or services that are configured to run inside the container. This allows the container to run multiple processes or services without having to manage them individually, and ensures that the container will keep running as long as supervisord is running.

# Note that the CMD instruction can be overridden at runtime by providing a different command to be executed when starting the container. For example, the command docker run my-image bash would override the CMD instruction and start a shell instead of supervisord.
CMD ["supervisord", "-n"]

# The EXPOSE instruction in a Dockerfile informs Docker that the container will listen on the specified network ports at runtime.

# In this case, the EXPOSE 80 443 3031 instruction exposes ports 80, 443, and 3031 for incoming network traffic. Port 80 is commonly used for HTTP traffic, port 443 is commonly used for HTTPS traffic, and port 3031 is not a well-known port and could be used for any custom application that requires it.

# Note that the EXPOSE instruction does not actually publish the specified ports or make them accessible from the host system or the outside world. It simply documents the ports that the container is listening on and provides a hint to users about how to configure network connections to the container.

# To actually publish and map these ports to the host system, you would need to use the -p or -P options with the docker run command, or specify the ports in a docker-compose.yml file.
EXPOSE 80 443 3031
