# aia-eia-js
FROM nodeshift/centos7-s2i-nodejs

# TODO: Set labels used in OpenShift to describe the builder image
LABEL io.k8s.display-name="AIA" \
      io.openshift.expose-services="8080:http" \
      io.openshift.tags="nodejs" \
      io.openshift.s2i.scripts-url="image:///usr/libexec/s2i" \
      maintainer="Franklin Gómez Otero <fgomezotero@gmail.com>"

# TODO: Copy the S2I scripts to /usr/libexec/s2i, since openshift/base-centos7 image
# sets io.openshift.s2i.scripts-url label that way, or update that label
COPY ./s2i/bin/ /usr/libexec/s2i

USER root

# TODO: Change permissions for run on Openshift
RUN chgrp -R 0 $APP_ROOT && \
    chmod -R g=u $APP_ROOT && \
    chmod g=u /etc/passwd

USER 1001

# TODO: Set the default CMD for the image
CMD ["/usr/libexec/s2i/usage"]
