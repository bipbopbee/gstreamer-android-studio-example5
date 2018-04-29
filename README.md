# gstreamer-android-studio-example5
Androidstudio gstreamer 坑很多，没要求的话还是用eclipse比较方便<br>
1.Android example 下载地址git://anongit.freedesktop.org/gstreamer/gst-docs<br>
 路径 gst-docs\examples\tutorials\android-tutorial-5<br>
2.下载预编译包地址 https://gstreamer.freedesktop.org/data/pkg/android/<br>
3.导入Androidstudio，因为是eclipse项目，所以要修改很多地方，详细步骤参考https://stackoverflow.com/questions/45044210/gstreamer-examples-in-android-studio<br>
4.build 如果出现gstreamer_android.so 找不到的错误： 修改build.gradle(app module):<br>
defaultConfig {
        applicationId "com.gst_sdk_tutorials.tutorial_5"
        minSdkVersion 9
        targetSdkVersion 14

        externalNativeBuild {
            ndkBuild {
                targets "tutorial-5"//这个把module改为targets
                abiFilters 'armeabi-v7a'
            }
        }
    }


编译第2步的预编译包<br>
1.git clone git://anongit.freedesktop.org/gstreamer/cerbero<br>
2.cd /cerbero<br>
3../cerbero-uninstalled -c config/cross-android-universal.cbc bootstrap<br>
4../cerbero-uninstalled -c config/cross-android-universal.cbc package gstreamer-1.0<br>
5.在cerbero/build/dist/android_universal/下就是各种abi架构的预编译包<br>
第4步每次执行都重新下载，可以修改build/source.py 115行增加redownload=False，不让其重新下载<br>。
如果第4步执行某个源码下载失败，可以复制下载地址，手动下载后复制到build/sources/local/相应目录，然后重新执行第4步。<br>
