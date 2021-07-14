# Stage 1
  - Start from the base image node:10
  - There are two package.json files: one is for nodejs server and another is for VueUI. We need to copy these into the Docker file system and install all the dependencies.
  - We need this step first to build images faster in case there is a change in the source later. We don’t want to repeat installing dependencies every time we change any source files.
  - Copy all the source files.
  - Vue uses CLI Service to build the app. So, install CLI and install all the dependencies.
  - Run npm run build to build the Vue App and all the assets will be created under dist a folder within a my-app folder.

# Stage 2
  - Start from the base image node:10
  - Take the build from stage 1 and copy all the files into ./my-app/dist folder.
  - Copy the nodejs package.json
  - Install all the dependencies
  - Finally, copy the server.js
  - Have this command node server.js with the CMD. This automatically runs when we run the image.


# build the image
docker build -t vue-node-image .
# check the images
docker images

# run the image
docker run -d -it -p  3080:3080 --name vue-node-ui vue-node-image
# check the container
docker ps

# You can exec into the running container with this command 
docker exec -it vue-node-ui /bin/sh

# Tại vì nodejs chỉ sử dụng bảng build nên chúng ta sẽ build rồi lấy các tập tin build đó bỏ vào, sẽ giảm dung lượng bằng image

# remove images 
- docker images -a list images 
- docker rmi Image Image


