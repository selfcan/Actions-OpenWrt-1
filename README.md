一、自用固件，B70和yk-l1集成了kmod-usb-audio和squeezelite-full，可以和Daphile或者Logitech media server(LMS)、roon core等组成双机播放系统（当然还要有个USB声卡才行）。
二、可以通过修改配置文件/etc/config/squeezelite，设置声卡、编码等参数：
/etc/config/squeezelite设置说明
config options 'options'   
option name 'squeezelite-studio'   #设置播放器名
option model_name 'SqueezeLite' #是播放器类型，不用改
option close_delay '0'
option priority '0'                           #进程优先级                  
option device 'hw:0,0'                    #声卡设备编号，默认hw:0,0，自动选取。
option decoder_auto_conf '1'
option dsd_over_pcm '0'                #播放DSD转码，dop
option stream_bufsiz '8192'           #缓冲
option out_bufsiz '8192'                #缓冲
option max_sr '48000'                   #解码器支持的最高码率，xmos可以设置位384000
option sr_delay '256'                     
option alsa_buffer '256'                #声卡缓冲，毫秒
option alsa_period '4'                   #the period count (values less than 50) or size in bytes (default 4 periods);
option alsa_format '16'                 #位深，xmos可以设置未24位
option alsa_mmap '0'
以上可以根据实际情况设置，以下是重点，
option server_addr '192.168.5.209'            #LMS等服务器的地址，根据实际填写。这个是重点，不加这一项，Daphile或者Logitech media server(LMS)、roon core等有可能发现不了这个的squeezelite播放器，我把一台玩客云刷Armbian后安装Logitech media server(LMS)没有写这一项，死活认不出squeezelite播放器，192.168.5.209是我的玩客云IP地址。
