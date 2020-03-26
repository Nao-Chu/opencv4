install opencv4



aliyun 

```
deb http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ bionic-backports main restricted universe multiverse
```



apt-get install 

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install cmake qt5-default libvtk6-dev zlib1g-dev libjpeg-dev libwebp-dev libpng-dev libtiff5-dev libopenexr-dev libgdal-dev libdc1394-22-dev libavcodec-dev libavformat-dev libswscale-dev libtheora-dev libvorbis-dev libxvidcore-dev libx264-dev yasm libopencore-amrnb-dev libopencore-amrwb-dev libv4l-dev libxine2-dev libtbb-dev libeigen3-dev doxygen libgtk2.0-dev pkg-config
```



cmake

```
cmake -DCMAKE_BUILD_TYPE=Release -DOPENCV_GENERATE_PKGCONFIG=ON -DCMAKE_INSTALL_PREFIX=/usr/local ..
```



make && make install

```
make -j4
sudo make install
```



config

```markdown
sudo sh -c 'echo "/usr/local/lib" >> /etc/ld.so.conf.d/opencv4.conf'
sudo ldconfig
```



Makefile

```makefile
cpp = g++
prom = main 
target = target
deps = $(shell find -name "*.h")
src  = $(shell find -name "*.cpp")
obj = $(src:%.cpp=%.o)
libs += $(shell pkg-config opencv4 --cflags --libs)
config = c++11
 
ALL = target
$(target): $(obj)
	$(cpp) -o $(prom) $(obj) -std=$(config) $(libs)

%.o: %.cpp $(deps)
	$(cpp) -c $< -o $@

clean:
	rm -rf $(obj) $(prom)
```

a