# Copyright 2016 The Kubernetes Authors.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

FROM centos:centos7

MAINTAINER chaizs@asiainfo.com

RUN yum install wget -y && \
	wget -r --no-parent -A epel-release-*.rpm https://dl.fedoraproject.org/pub/epel/7/x86_64/Packages/e/ && \
	rpm -Uvh dl.fedoraproject.org/pub/epel/7/x86_64/Packages/e/epel-release-*.rpm && \
	yum install redis -y && \
	yum clean all && \
	rm -rf /var/cache/yum && \
	mkdir -p /redis-sentinel
	#chmod -R 777 /redis-sentinel /redis-slave

COPY redis-master.conf /redis-master/redis.conf
COPY redis-slave.conf /redis-slave/redis.conf
COPY run.sh /run.sh

CMD [ "/run.sh" ]

ENTRYPOINT [ "bash", "-c" ]
