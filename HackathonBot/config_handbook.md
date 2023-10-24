# 配置使用手册

## 总体概述
为了监控多个快乐开源任务，可以在`config.py`文件下指定多个开源任务配置。

## 配置使用方式
配置分为两种，一种是基础配置`common_config`，包括多个任务共用的一些信息，比如`用户token`等信息，每个字段的具体含义如下：
* issue_token：具有修改`issue`权限的`token`。
* comment_token: 具有评论权限的`token`。
* proxies：代理地址。
* board: 是否展示看板信息，默认展示。
* comment_to_user_list：对于报名格式不正确用户的保存，保持为空即可。

除了基础配置，每个任务都会有一个特有的配置对象，该对象每个字段的含义如下：
* issue_name：任务名称，用于标识任务。
* start_time：任务开始时间，只会统计开始时间之后的PR(注意时间中的字母T和Z不能缺少)。
* issue_url：黑客松 `issue`页面 `url` 地址, 注意结尾不要有斜杠，前缀为`api.github.com`。
* repo_urls：监控的仓库列表。
* un_handle_tasks： 忽略不处理的题号，这部分留给人工处理。
* removed_tasks：已删除的赛题。
* type_names： 赛道名，一个开源任务可以有一个或多个赛道。
* task_types：每个赛题所属的赛道，每个赛道是一个数组，对于多个赛题，数组中可以使用横线标识区间，比如 `['1-20']`表示赛题1到20。
* pr_prefix: `PR`标题所要包含的前缀。
* pr_col：PR、状态等信息所在的列。
* complete_col: 如果需要标识完成人，需要写上完成人所在的列。

> 可以在特定配置对象中覆盖基础配置中的属性，即两个配置对象都配置了同一字段，则会以特定配置对象中字段为准。

## issue编写注意事项
* `issue` 中任务表格的题号前后必须只能有一个空格，如 `| 1 |`。
* `issue` 中最好有`看板信息`这几个字，并且在后面接上`回车 + #####`这个特殊标志，否则看板信息会加在`issue`内容的最后。