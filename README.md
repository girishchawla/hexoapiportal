# hexoapiportal

This is a high level prototype for a Hexo powered API Developer portal.
Many teams do not need an API Management Layer. They just need an API Documentation
portal with 1) Authentication/Authorization/Sign-up 2) API Token generation/expiry 3) A support page
This is an attempt to show the building blocks. The Back-end implementation in terms of database
persitence for the above forms has been left to the user to implement.

# Install hexo cli

npm install hexo-cli -g

git clone https://github.com/girishchawla/hexoapiportal.git

npm install

hexo server  ( The Webserver will start at http://hostname:11000)

# Use widdershins or any other utility to generate Markdown file from OpenAPI 2.0 or 3.0 specs

Install Widdershins

https://github.com/Mermade/widdershins

Use widdershins to generate Markdown files with the following command. ( File paths are examples)

node widdershins  -e ./widdershins/whiteboard_env.json $FILE_PATH_TO_API_SPEC/swagger.json -o $FILE_PATH_TO_PORTAL/source/amadeus/index.md

Widdershins can be found at https://github.com/Mermade/widdershins

# Other details

The Login/Registration, Support and API Token Management Pages  are just pass through and
do not have a database behind them

The login page is accessible from http://hostname:11000
Users can change the themes and layouts of the pages and documentation by learning more
about the hexo framework at hexo.io. Some youtube videos can be found at
https://www.youtube.com/watch?v=Kt7u5kr_P5o&list=PLLAZ4kZ9dFpOMJR6D25ishrSedvsguVSm

