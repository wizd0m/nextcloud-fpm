#
# Dockerfile for building own Collabora/CODE
#

FROM ubuntu:16.04

ENV domain localhost
ENV LC_CTYPE th_TH.UTF-8

RUN set -eux; \
	\
        sed -i 's/archive/th.archive/g' /etc/apt/sources.list \
        && apt-get update \ 
        && apt-get install -y --no-install-recommends \
        apt-transport-https \
        locales-all \
        && echo "deb [trusted=yes] https://collaboraoffice.com/repos/CollaboraOnline/CODE /" >> /etc/apt/sources.list.d/collabora.list \
        && apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 6CCEA47B2281732DF5D504D00C54D189F4BA284D \
        && apt-get install -y wget \
        && wget --no-check-certificate -O /var/lib/apt/lists/collaboraoffice.com_repos_CollaboraOnline_CODE_InRelease https://www.collaboraoffice.com/repos/CollaboraOnline/CODE/InRelease \
        && apt-get update --fix-missing \
        && apt-get install -y --no-install-recommends loolwsd \
        code-brand \
        collaboraoffice6.0 \
        collaboraoffice6.0-ure* \
        collaboraoffice6.0-dict-en* \
        collaboraofficebasis6.0-core* \
        collaboraofficebasis6.0-calc* \
        collaboraofficebasis6.0-graphicfilter* \
        collaboraofficebasis6.0-images* \
        collaboraofficebasis6.0-impress* \
        collaboraofficebasis6.0-ooofonts* \
        collaboraofficebasis6.0-writer* \
        inotify-tools \
        psmisc \
#       && echo ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true | debconf-set-selections \
#       && apt-get install -y --no-install-recommends ttf-mscorefonts-installer \
#       && apt-get remove -y wget \
        && apt-get purge -y wget \
        && apt-get clean && rm -rf /var/lib/apt/list/* /tmp/* /var/tmp/*
				
EXPOSE 9980

COPY ./script/start-libreoffice.sh /

RUN chmod +x /start-libreoffice.sh 

CMD bash start-libreoffice.sh