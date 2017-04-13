# 生成Android设备唯一识别码
通过多种方式生成设备的唯一标识符并存储到手机中


#### UUID
全局唯一标识符,是指在一台机器上生成的数字，它保证对在同一时空中的所有机器都是唯一的。
#### IMEI
是国际移动设备身份码的缩写，国际移动装备辨识码，是由15位数字组成的"电子串号"，它与每台手机一一对应，而且该码是全世界唯一的。
#### MEID
是全球唯一的56bit CDMA制式移动终端标识号。标识号会被烧入终端里，并且不能被修改。可用来对CDMA制式移动式设备进行身份识别和跟踪。
#### DEVICE_ID
根据不同的手机设备返回IMEI，MEID或者ESN码。非手机设备无效
#### MAC ADDRESS
可以使用手机WiFi或蓝牙的MAC地址作为设备标识，但是并不推荐这么做，原因有以下两点：

硬件限制：并不是所有的设备都有WiFi和蓝牙硬件，硬件不存在自然也就得不到这一信息。

获取的限制：如果WiFi没有打开过，是无法获取其Mac地址的；而蓝牙是只有在打开的时候才能获取到其Mac地址。
#### ANDROID_ID
ANDROID_ID是设备第一次启动时产生和存储的64bit的一个数，当设备被wipe后该数重置。
------------------------------------------------
### 最终方法
为了实现在设备上更通用的获取设备唯一标识，我们可以，以ANDROID_ID为基础，在获取失败时以TelephonyManager.getDeviceId()为备选方法，如果再失败，使用UUID的生成策略。
