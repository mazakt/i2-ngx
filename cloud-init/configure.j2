#!/bin/bash

set -e
set -x


#
# Variables passed from pipeline (Jinja2)
#
DC={{ dc }}
PRODUCT={{ product }}
ENVIRONMENT={{ product_environment }}


#
# Application installation and configuration
#
yum install -y epel-release
yum install -y nginx jq

systemctl enable nginx
systemctl start nginx

cat > /usr/share/nginx/html/index.html <<EOF
<html>
  <head>
    <title>${PRODUCT} -- cloud-init proof of concept</title>
  </head>
  <body>
    <h1>${PRODUCT} -- cloud-init proof of concept</h1>
    <p>Welcome to $(hostname)</p>
    <p>This VM was <strong>originally deployed by a pipeline</strong></p>
  </body>
</html>
EOF


#
# Simulate the roll-in logic
#
pipeline_status=`curl -s http://169.254.169.254/openstack/latest/meta_data.json | jq -r .meta.pipeline_status`
if [ "$pipeline_status" != "in_progress" ]; then
    sed -i 's/originally deployed by a pipeline/evacuated and rebuilt/' /usr/share/nginx/html/index.html
fi

