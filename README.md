[![GPL 3.0 license](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](https://github.com/REIJI007/AdBlock_Rule_For_Clash/blob/main/LICENSE-GPL3.0)
[![CC BY-NC-SA 4.0 license](https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg)](https://github.com/REIJI007/AdBlock_Rule_For_Clash/blob/main/LICENSE-CC%20BY-NC-SA%204.0)
<!-- 居中的大标题 -->
<h1 align="center" style="font-size: 70px; margin-bottom: 20px;">AdBlock_Rule_For_Clash</h1>

<!-- 居中的副标题 -->
<h2 align="center" style="font-size: 30px; margin-bottom: 40px;">一个适用于Clash（premium核心与mihomo核心）的广告域名拦截rule-providers规则集</h2>

<!-- 徽章（根据需要调整） -->
<p align="center" style="margin-bottom: 40px;">
    <img src="https://img.shields.io/badge/last%20commit-today-brightgreen" alt="last commit" style="margin-right: 10px;">
    <img src="https://img.shields.io/github/forks/REIJI007/AdBlock_Rule_For_Clash" alt="forks" style="margin-right: 10px;">
    <img src="https://img.shields.io/github/stars/REIJI007/AdBlock_Rule_For_Clash" alt="stars" style="margin-right: 10px;">
    <img src="https://img.shields.io/github/issues/REIJI007/AdBlock_Rule_For_Clash" alt="issues" style="margin-right: 10px;">
    <img src="https://img.shields.io/github/license/REIJI007/AdBlock_Rule_For_Clash" alt="license" style="margin-right: 10px;">
</p>

**一、从多个广告过滤器中提取拦截域名条目，删除重复项，并将它们转换为兼容Clash的payload列表格式，其中列表的每一项都写成了符合clash的Matcher Ruleset格式数组，一行仅一条规则。该列表可以用作Clash的rule-providers，以阻止广告域名， powershell脚本每20分钟自动执行并将生成的文件发布在release中.五个文件的下载地址分别如下，其中adblock_reject.yaml和adblock_reject.txt是Matcher Ruleset格式数组构成的payload列表（直接作为外部规则集rule-providers使用），adblock_reject_change.yaml和adblock_reject_change.txt则是纯粹的Matcher Ruleset数组列表（需要复制到rules配置使用），adblock_reject.mrs则是由mihomo核心将adblock_reject.yaml转化得来的规则集，adblock_reject_change.txt则是由adblock_reject_change.txt经过修改得到**
<br>
<br>
**前三个是适用于Clash的外部远程规则集（payload列表）**
<br>
*1、YAML格式的外部远程拦截域名规则集 adblock_reject.yaml* 
<br>
*https://raw.githubusercontent.com/REIJI007/AdBlock_Rule_For_Clash/main/adblock_reject.yaml*
*https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Clash@main/adblock_reject.yaml*


*2、MRS格式的外部远程拦截域名规则集 adblock_reject.mrs* 
<br>
*https://raw.githubusercontent.com/REIJI007/AdBlock_Rule_For_Clash/main/adblock_reject.mrs*
*https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Clash@main/adblock_reject.mrs*


*3、文本格式的外部远程拦截域名规则集 adblock_reject.txt* 
<br>
*https://raw.githubusercontent.com/REIJI007/AdBlock_Rule_For_Clash/main/adblock_reject.txt*
*https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Clash@main/adblock_reject.txt*



**这两个是适用于Clash的Matcher Ruleset数组列表，两个文件除了拓展名不一样，内容是一样的，你可打开然后复制粘贴到你的yaml配置文件下的rules字段，注意对齐**
<br>
*4、YMAL格式的外部拦截域名Matcher Ruleset条目列表 adblock_reject_change.yaml* 
<br>
*https://raw.githubusercontent.com/REIJI007/AdBlock_Rule_For_Clash/main/adblock_reject_change.yaml*
*https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Clash@main/adblock_reject_change.yaml*



*5、文本格式的外部拦截域名Matcher Ruleset条目列表 adblock_reject_change.txt* 
<br>
*https://raw.githubusercontent.com/REIJI007/AdBlock_Rule_For_Clash/main/adblock_reject_change.txt*
*https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Clash@main/adblock_reject_change.txt*



**最后一个是适用于Surge的Matcher Ruleset数组列表** 
<br>
*6、使用于Surged1外部拦截域名Matcher Ruleset条目列表 adblock_reject_surge.txt* 
<br>
*https://raw.githubusercontent.com/REIJI007/AdBlock_Rule_For_Clash/main/adblock_reject_surge.txt*
*https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Clash@main/adblock_reject_surge.txt*



**二、理论上任何代理拦截域名且符合广告过滤器过滤语法的列表订阅URL都可加入此powershell脚本处理，请自行酌情添加过滤器订阅URL至adblock_rule_generator_yaml.ps1或者adblock_rule_generator_txt.ps1脚本中进行处理，你可将该脚本代码复制到本地文本编辑器制作成.ps1后缀的文件运行在powershell上，注意修改生成的yaml文件路径，最后在clash的yaml配置中实现调用本地生成的yaml文件或者mrs文件作为rule-providers)，且clash配置字段写成类似于如下两个例子（若要使用mihomo的.mrs格式配置文件则用下面这个），如果是作为Surge的配置则使用最后一个**
<br>
<br>
*简而言之就是可以让你DIY出希望得到的拦截域名payload列表，缺点是此做法只适合本地定制使用，当然你也可以像本仓库一样部署到GitHub上面，见仁见智*


```conf
#YAML格式外部本地拦截域名规则集
rule-providers:
  adblock:
    type: file
    behavior: domain
    format: yaml
    path: C:\Users\YourUsername\Documents\file.yaml   #你的YAML格式外部本地拦截域名rule-providers规则集文件保存路径
    
rules:
  - RULE-SET,adblock,REJECT
```
```conf
#MRS格式外部本地拦截域名规则集,适用于mihomo核心
rule-providers:
  adblock:
    type: file
    behavior: domain
    format: mrs
    path: C:\Users\YourUsername\Documents\file.mrs   #你的MRS格式外部本地拦截域名rule-providers规则集文件保存路径
    
rules:
  - RULE-SET,adblock,REJECT
```
```conf
#TEXT格式外部本地拦截域名规则集,适用于mihomo核心
rule-providers:
  adblock:
    type: file
    behavior: domain
    format: text
    path: C:\Users\YourUsername\Documents\file.txt   #你的TEXT格式外部本地拦截域名rule-providers规则集文件保存路径
    
rules:
  - RULE-SET,adblock,REJECT
```
```conf
#适用于Surge的本地拦截域名规则集
[Rule]
RULE-SET,C:\Users\YourUsername\Documents\file.txt,policy=REJECT
```



        


**三、本仓库引用多个广告过滤器，从这些广告过滤器中提取了被拦截条目的域名，剔除了非拦截项并去重，最后做成payload列表，虽无法做到全面保护但能减少广告带来的困扰，请自行斟酌考虑使用。本仓库采取域名完全匹配策略，即匹配到于拦截列表上的域名完全一致时触发拦截，除此之外的情况给予放行**


**四、关于本仓库使用方式：**

  *使用方式一：下载releases中的adblock_reject_change.txt文件，里面的内容可直接粘贴到clash的yaml配置中的rules字段下作为拦截规则（需要手动下载更新），adblock_reject_change.yaml则可以直接保存作为本地rule-providers，压缩包的两个powershell脚本分别用来生成adblock_reject.txt和adblock_reject.yaml,使用脚本前应当自行先将脚本内的文件生成路径填入其中*



  *使用方式二：将下面对应格式的配置文件中rule-providers字段和rules字段内容添加到你的配置文件充当远程规则集，需要特别注意配置文件的缩进和对齐（同步本仓库的云端部署的远程规则集配置)*



```conf
#YAML格式外部远程拦截域名规则集
rule-providers:
  adblock:
    type: http
    behavior: domain
    format: yaml
    url: https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Clash@main/adblock_reject.yaml
    path: ./ruleset/adblock_reject.yaml
    interval: 120
    
rules:
  - RULE-SET,adblock,REJECT
```

```conf
#MRS格式外部远程拦截域名规则集
rule-providers:
  adblock:
    type: http
    behavior: domain
    format: mrs
    url: https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Clash@main/adblock_reject.mrs
    path: ./ruleset/adblock_reject.mrs
    interval: 120
    
rules:
  - RULE-SET,adblock,REJECT
```

```conf
#TEXT格式外部远程拦截域名规则集
rule-providers:
  adblock:
    type: http
    behavior: domain
    format: txt
    url: https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Clash@main/adblock_reject.txt
    path: ./ruleset/adblock_reject.txt
    interval: 120
    
rules:
  - RULE-SET,adblock,REJECT
```
```conf
#适用于Surge的远程拦截域名规则集
[Rule]
RULE-SET,https://cdn.jsdelivr.net/gh/REIJI007/AdBlock_Rule_For_Clash@main/adblock_reject_surge.txt,policy=REJECT
```





**五、关于本仓库的使用效果为什么没有普通广告过滤器效果好的疑问解答：**
<br>
*因为普通的广告过滤器包含域名过滤（拦截广告域名）、路径过滤（例如拦截URL路径中包含/ads/的所有请求）、正则表达式过滤（例如拦截所有包含ads.js或ad.js的URL）、类型过滤（例如只拦截图片资源）、隐藏元素等等多因素作用下使得在广告拦截测试网站中可以取得高分。**但碍于clash内核的路由模式（可参考相关内核文档）**，本仓库仅提取了被拦截域名进行域名完全匹配过滤，换言之，本仓库就是一个“删减版”的广告过滤器（仅保留了域名完全匹配过滤功能，规则数在25万条左右），所以最终效果没有广告过滤器效果好*




**六、本仓库引用的广告过滤规则来源请查看Referencing rule sources.txt，后续考虑添加更多上游规则列表进行处理整合（目前32个来源）。至于是否误杀域名完全取决于这些处于上游的广告过滤器的域名拦截行为，若不满意的话可按照第二条在本地使用adblock_rule_generator_yaml.ps1或者adblock_rule_generator_txt.ps1两个脚本进行DIY本地定制化，亦或可以像本仓库一样DIY定制后部署到github上面，或者fork本仓库自行DIY**


**七、特别鸣谢**

1、anti-AD (https://github.com/privacy-protection-tools/anti-AD)

2、easylist (https://github.com/easylist/easylist)

3、cjxlist (https://github.com/cjx82630/cjxlist)

4、uniartisan (https://github.com/uniartisan/adblock_list)

5、Cats-Team (https://github.com/Cats-Team/AdRules)

6、217heidai (https://github.com/217heidai/adblockfilters)

7、GOODBYEADS (https://github.com/8680/GOODBYEADS)

8、AWAvenue-Ads-Rule (https://github.com/TG-Twilight/AWAvenue-Ads-Rule)

9、Bibaiji (https://github.com/Bibaiji/ad-rules/)

10、uBlockOrigin (https://github.com/uBlockOrigin/uAssets)

11、ADguardTeam (https://github.com/AdguardTeam/AdGuardFilters)

12、HyperADRules (https://github.com/Lynricsy/HyperADRules)

## License

Attribution-NonCommercial-ShareAlike 4.0 International (CC BY-NC-SA 4.0)
