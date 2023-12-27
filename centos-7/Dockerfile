FROM docker.io/centos:7.9.2009

LABEL org.opencontainers.image.description="CentOS container for Molecule"
LABEL org.opencontainers.image.source=https://github.com/hspaans/molecule-containers

# Configure apt and install packages
# hadolint ignore=DL3031,DL3033
RUN yum makecache fast \
    && yum -y install python3 deltarpm epel-releas \
    && yum -y update \
    # Clean up
    && yum clean all

# Make sure systemd doesn't start agettys on tty[1-6].
RUN rm -f /lib/systemd/system/multi-user.target.wants/getty.target

VOLUME ["/sys/fs/cgroup"]

CMD ["/lib/systemd/systemd"]