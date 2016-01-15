## 转换dmesg的date：
dmesg|tail -1000f | sed -r 's#^\[([0-9]+\.[0-9]+)\](.*)#echo -n "[";echo -n $(date --date="@$(echo "$(grep btime /proc/stat|cut -d " " -f 2)+\1" | bc)" +"%c");echo -n "]";echo -n "\2"#e' | less -M

* [dmesg to human date](http://stackoverflow.com/questions/13890789/convert-dmesg-timestamp-to-custom-date-format)
