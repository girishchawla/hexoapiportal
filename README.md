# hexoapiportal

Install Widdershins

https://github.com/Mermade/widdershins


# Install hexo cli

npm install hexo-cli -g

git clone https://github.com/girishchawla/hexoapiportal.git

npm install

hexo server  ( The Webserver will start at http://hostname:11000)

# Use widdershins or any other utility to generate Markdown file from OpenAPI 2.0 or 3.0 specs

Use widdershins to generate Markdown files with the following command. ( File paths are examples)

node widdershins  -e ./widdershins/whiteboard_env.json $FILE_PATH_TO_API_SPEC/swagger.json -o $FILE_PATH_TO_PORTAL/source/amadeus/index.md

Widdershins can be found at https://github.com/Mermade/widdershins

# Other details

The Login/Registration Pages at http://hostname:11000 are just pass through

The Support Page does not have a database behind the form.

The API Token generator page also does not have a database behind it.

