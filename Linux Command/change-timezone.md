# Change to Vietname Timezone
```
# first you should backup your /etc/localtime 
$> sudo cp /etc/localtime /etc/localtime.old

# create a soft link of timezone you want to use to /etc/localtime
$> sudo ln -sf /usr/share/zoneinfo/Asia/Ho_Chi_Minh /etc/localtime

# check the result
$> date
Mon Jun 25 20:26:02 ICT 2012
```