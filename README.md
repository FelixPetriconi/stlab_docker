
#How to create docker image
cd gcc5_boost_1.66.0
docker build -t gcc-5.5_boost-1.66 .

#How to run docker with open bash
docker run -it -v ~/github/future_library/:/future_library gcc-5.5_boost-1.66 bash


