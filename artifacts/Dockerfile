FROM nginx

# can be passed during Docker build as build time environment for github branch to pickup configuration from.
ARG container_user=mosip

# can be passed during Docker build as build time environment for github branch to pickup configuration from.
ARG container_user_group=mosip

# can be passed during Docker build as build time environment for github branch to pickup configuration from.
ARG container_user_uid=1001

# can be passed during Docker build as build time environment for github branch to pickup configuration from.
ARG container_user_gid=1001

# install packages and create user
RUN apt-get -y update &&\
apt-get install -y unzip wget zip &&\
groupadd -g ${container_user_gid} ${container_user_group} &&\
useradd -u ${container_user_uid} -g ${container_user_group} -s /bin/sh -m ${container_user} \
&& mkdir -p /var/run/nginx /var/tmp/nginx \
&& chown -R ${container_user}:${container_user} /usr/share/nginx /var/run/nginx /var/tmp/nginx

COPY ./nginx.conf /etc/nginx/nginx.conf

# set working directory for the user
WORKDIR /home/${container_user}

ENV work_dir=/home/${container_user}

# environment variable for basepath
ENV base_path=/usr/share/nginx/html/artifactory

# environment variable for Biosdk client Zip path
ENV biosdk_client_zip_path=${base_path}/libs-release-local/biosdk/mock/0.9

# environment variable for Demosdk Zip path
ENV demosdk_zip_path=${base_path}/libs-release-local/demosdk/default/

# environment variable for Biosdk lib Zip path
ENV biosdk_lib_zip_path=${base_path}/libs-release-local/biosdk/

# environment variable for Cache Provider Jar path
ENV cache_path=${base_path}/libs-release-local/cache

# environment variable for ida shell scripts path
ENV ida_sh_path=${base_path}/libs-release-local/deployment/docker/id-authentication

# environment variable for hsm client path
ENV hsm_client_path=${base_path}/libs-release-local/hsm

# environment valiable for sdk jar
ENV sdk_path=${base_path}/libs-release-local/mock-sdk/1.1.5/

# environment variable for Kernel Jars
ENV kernel_jar_path=${base_path}/libs-release-local/io/mosip/kernel

# environment variable for regproc reprocessor ceylon cache jar path
ENV test_jar_path=${base_path}/libs-release-local/io/mosip/testing/

# environment variable for ref-idobjectvalidator jar
ENV idobject_jar_path=${base_path}/libs-release-local/io/mosip/kernel/kernel-ref-idobjectvalidator


# environment variable for prereg transliteration jar path
ENV icu4j_jar_path=${base_path}/libs-release-local/icu4j

# environment variable for i18n zip path
ENV i18n_zip_path=${base_path}/libs-release-local/i18n

# environment variable for Clamav dependency
ENV clamav_path=${base_path}/libs-release-local/clamav

ENV regclient_jar_path=${base_path}/libs-release-local

# environment variable for child auth filter jar path
ENV child_auth_filter_jar_path=${base_path}/libs-release-local/io/mosip/authentication/authentication-ref-impl

# environment variable for jar version to be downloaed, this needed to be passed buildtime
ENV version=1.2.0

ENV master_template_path=${base_path}/libs-release-local/master-templates

# environment variable for maven central mosip artifacts 
ENV release_maven_path=https://repo1.maven.org/maven2/io/mosip

# environment variable for maven central auth adapter. In case released uncomment this and comment out below duplicate one.
ENV auth_adapter_jar_url_env=${release_maven_path}/kernel/kernel-auth-adapter/${version}/kernel-auth-adapter-${version}.jar
#ENV auth_adapter_jar_url_env=https://oss.sonatype.org/content/repositories/snapshots/io/mosip/kernel/kernel-auth-adapter/${version}/kernel-auth-adapter-1.2.0-rc2-20220125.115113-47.jar

# environment variable for msg91_jar url. 
ENV sms_msg91_url_env=${release_maven_path}/kernel/kernel-smsserviceprovider-msg91/${version}/kernel-smsserviceprovider-msg91-${version}.jar
#ENV sms_msg91_url_env=https://oss.sonatype.org/service/local/repositories/snapshots/content/io/mosip/kernel/kernel-smsserviceprovider-msg91/${version}/kernel-smsserviceprovider-msg91-1.2.0-rc2-20220125.123650-293.jar

# environment variable for ref-idobjectvalidator_jar url
ENV ref_idobjectvalidator_jar_url_env=${release_maven_path}/kernel/kernel-ref-idobjectvalidator/${version}/kernel-ref-idobjectvalidator-${version}.jar
#ENV ref_idobjectvalidator_jar_url_env=https://oss.sonatype.org/service/local/repositories/snapshots/content/io/mosip/kernel/kernel-ref-idobjectvalidator/${version}/kernel-ref-idobjectvalidator-1.2.0-rc2-20220125.123650-293.jar

# environment variable for clamav jar and client url
#ENV clamav_jar_url_env=https://oss.sonatype.org/service/local/repositories/snapshots/content/io/mosip/kernel/kernel-virusscanner-clamav/${version}/kernel-virusscanner-clamav-1.2.0-rc2-20220125.123650-90.jar
ENV clamav_jar_url_env=${release_maven_path}/kernel/kernel-virusscanner-clamav/${version}/kernel-virusscanner-clamav-${version}.jar

ENV clamav_client_url_env=https://oss.sonatype.org/service/local/repositories/releases/content/xyz/capybara/clamav-client/1.0.4/clamav-client-1.0.4.jar

# environment variable for sdk url
#ENV sdk_jar_url_env=https://oss.sonatype.org/service/local/repositories/snapshots/content/io/mosip/mock/sdk/mock-sdk/1.2.0-SNAPSHOT/mock-sdk-1.2.0-20210916.072002-15.jar
ENV sdk_jar_url_env=${release_maven_path}/mock/sdk/mock-sdk/${version}/mock-sdk-${version}.jar

# environment variable for cache URL 
ENV cache_url_env=${release_maven_path}/cacheprovider/cache-provider-hazelcast/${version}/cache-provider-hazelcast-${version}.jar

# environment variable for biosdk client jar URL
#ENV biosdk_client_url_env=https://oss.sonatype.org/service/local/repositories/snapshots/content/io/mosip/biosdk/biosdk-client/${version}/biosdk-client-1.2.0-rc2-20220125.123659-97-jar-with-dependencies.jar
ENV biosdk_client_url_env=${release_maven_path}/biosdk/biosdk-client/${version}/biosdk-client-${version}-jar-with-dependencies.jar

# environment variable for demosdk jar URL
#ENV demosdk_jar_url_env=https://oss.sonatype.org/service/local/repositories/snapshots/content/io/mosip/demosdk/demosdk/${version}/demosdk-1.2.0-rc2-20220125.123533-97-jar-with-dependencies.jar
ENV demosdk_jar_url_env=${release_maven_path}/demosdk/demosdk/${version}/demosdk-${version}-jar-with-dependencies.jar

# environment variable for child authentication filter jar URL
#ENV child_auth_filter_jar_url=https://oss.sonatype.org/service/local/repositories/snapshots/content/io/mosip/authentication/authentication-childauthfilter-impl/${version}/authentication-childauthfilter-impl-1.2.0-rc2-20210923.113606-11.jar
ENV child_auth_filter_jar_url=${release_maven_path}/authentication/authentication-childauthfilter-impl/${version}/authentication-childauthfilter-impl-${version}.jar

# Create all the Jar paths
RUN mkdir -p ${biosdk_client_zip_path}/biosdk-client ${demosdk_zip_path}/demosdk ${biosdk_lib_zip_path}/biosdk-lib ${cache_path} ${ida_sh_path} ${hsm_client_path} ${kernel_jar_path} ${test_jar_path} ${idobject_jar_path} ${sdk_path} ${icu4j_jar_path} ${clamav_path} ${i18n_zip_path} ${child_auth_filter_jar_path} ${base_path}/libs-release-local/reg-client ${master_template_path}

# Copy all the respective jars to the location

COPY /src/sdk/biosdk/install.sh ${biosdk_client_zip_path}/biosdk-client/

COPY /src/sdk/demosdk/install.sh ${demosdk_zip_path}/demosdk/

COPY /src/deployment/docker/id-authentication/* ${ida_sh_path}/

COPY /src/hsm/client.zip ${hsm_client_path}/

COPY /src/testing/regproc-reprocessor-ceylon-cache-repo.zip ${test_jar_path}/

COPY /src/testing/glowroot.zip ${test_jar_path}/

COPY /src/i18n/regclient-i18n-bundle/*  ${work_dir}/resources/

COPY /src/i18n/admin-entity-spec-bundle/*  ${work_dir}/admin-entity-spec-bundle/

COPY /src/i18n/admin-i18n-bundle/*  ${work_dir}/admin-i18n-bundle/

COPY /src/i18n/pmp-entity-spec-bundle/*  ${work_dir}/pmp-entity-spec-bundle/

COPY /src/i18n/pmp-i18n-bundle/*  ${work_dir}/pmp-i18n-bundle/

COPY /src/i18n/pre-registration-i18n-bundle/*  ${work_dir}/pre-registration-i18n-bundle/

COPY /src/master-templates/* ${work_dir}/master-templates/

RUN zip -r -j ${base_path}/libs-release-local/reg-client/resources.zip ${work_dir}/resources  && \
zip -r -j ${i18n_zip_path}/admin-entity-spec-bundle.zip ${work_dir}/admin-entity-spec-bundle/*  && \
zip -r -j ${i18n_zip_path}/admin-i18n-bundle.zip ${work_dir}/admin-i18n-bundle/*  && \
zip -r -j ${i18n_zip_path}/pmp-entity-spec-bundle.zip ${work_dir}/pmp-entity-spec-bundle/*  && \
zip -r -j ${i18n_zip_path}/pmp-i18n-bundle.zip ${work_dir}/pmp-i18n-bundle/*  && \
zip -r -j ${i18n_zip_path}/pre-registration-i18n-bundle.zip ${work_dir}/pre-registration-i18n-bundle/* && \
zip -r -j ${master_template_path}/master-templates.zip ${work_dir}/master-templates/*

COPY /src/jre/zulu11.41.23-ca-fx-jre11.0.8-win_x64.zip ${regclient_jar_path}/zulu11.41.23-ca-fx-jre11.0.8-win_x64.zip

#COPY /src/i18n/pre-registration-i18n-bundle.zip ${i18n_zip_path}/

#COPY /src/i18n/admin-entity-spec-bundle.zip ${i18n_zip_path}/

#COPY /src/i18n/admin-i18n-bundle.zip ${i18n_zip_path}/

COPY /src/icu4j/* ${icu4j_jar_path}/


# Download required respective all the jars and create biosdk zip

RUN wget ${auth_adapter_jar_url_env} -O ${kernel_jar_path}/kernel-auth-adapter.jar  &&\

echo "Downloaded auth adapter jar" &&\

wget ${sms_msg91_url_env} -O ${kernel_jar_path}/kernel-smsserviceprovider-msg91.jar  &&\

echo "Downloaded msg91 jar" &&\

wget ${ref_idobjectvalidator_jar_url_env} -O ${idobject_jar_path}/kernel-ref-idobjectvalidator.jar &&\

echo "Downloaded idobjectvalidator jar" &&\

wget ${cache_url_env} -O ${cache_path}/cache-provider.jar &&\

echo "Downloaded hazlecast cache jar" &&\

wget ${sdk_jar_url_env} -O ${sdk_path}/mock-sdk.jar &&\

echo "Downloaded Mock-sdk-jar" &&\

wget ${clamav_jar_url_env} -O ${clamav_path}/kernel-virusscanner-clamav.jar &&\

echo "Downloaded ClamAV jar" &&\

wget ${clamav_client_url_env} -O ${clamav_path}/clamav.jar &&\

echo "Downloaded ClamAV client" &&\

wget ${biosdk_client_url_env} -P ${biosdk_client_zip_path}/biosdk-client/ &&\

echo "Downloaded biosdk client creating the zip" &&\

zip -r -j ${biosdk_client_zip_path}/biosdk-client.zip ${biosdk_client_zip_path}/biosdk-client/* &&\

echo "zip creation completed" &&\

rm -rf ${biosdk_client_zip_path}/biosdk-client &&\

echo "folder biosdk client deleted" &&\

wget ${sdk_jar_url_env} -P ${biosdk_lib_zip_path}/biosdk-lib/ &&\

zip -r -j ${biosdk_lib_zip_path}/biosdk-lib.zip ${biosdk_lib_zip_path}/biosdk-lib/* &&\

rm -rf ${biosdk_lib_zip_path}/biosdk-lib &&\

echo "biosdk lib zip created" &&\

wget ${demosdk_jar_url_env} -P ${demosdk_zip_path}/demosdk/ &&\

echo "Downloaded demosdk jar with dependency creating the zip" &&\

zip -r -j ${demosdk_zip_path}/demosdk.zip ${demosdk_zip_path}/demosdk/* &&\

echo "zip creation completed" &&\

rm -rf ${demosdk_zip_path}/demosdk &&\

echo "folder demosdk deleted" &&\

wget ${child_auth_filter_jar_url} -O ${child_auth_filter_jar_path}/authentication-childauthfilter-impl.jar &&\

echo "Downloaded Child Auth Filter Jar"


RUN sed -i -e '/listen/!b' -e '/80;/!b' -e 's/80;/8080;/' /etc/nginx/conf.d/default.conf

# select container user for all tasks
USER ${container_user_uid}:${container_user_gid}

EXPOSE 8080

CMD ["nginx", "-g", "daemon off;"]
