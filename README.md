# hexoapiportal

Install Widdershins

https://github.com/Mermade/widdershins


# Install hexo cli

npm install hexo-cli -g


git clone https://github.com/girishchawla/hexoapiportal.git

npm install

hexo server  ( The Webserver will start at http://hostname:11000)

Use widdershins to generate Markdown files with the following command. ( File paths are examples)

node widdershins  -e ./widdershins/whiteboard_env.json $FILE_PATH_TO_API_SPEC/swagger.json -o $FILE_PATH_TO_PORTAL/source/amadeus/index.md

The Login and Registration Pages at http://hostname:11000 are just pass through

