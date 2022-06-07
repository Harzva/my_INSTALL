
```
def uploadToSVN(self, ret_excel_time):
 
	# upload xls file SVN
	filename = "result_" + ret_excel_time + ".xls"
	print "\n Upload xls file to SVN : --> \nsvn://192.168.xxx.xxx/trunk/data/sweepsCrawlerData/" + filename + "\n"
 
	#svn resolved %s & \
	#svn commit -m '' %s & \
	#svn update & \
	#svn revert %s & \
	cmd = '''start E:\sweepstake_site_crawlers\data\\result & \
	E: & \
	cd E:\sweepstake_site_crawlers\data\\result & \
	svn cleanup & \
	svn add %s & \
	svn resolved %s & \
	svn commit -m '' %s & \
	svn update & \
	''' % (filename,filename,filename)
	
	os.system(cmd)
```
