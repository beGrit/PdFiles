1. [课程接口](#kc_interface)

2. [学习记录接口](#xxjl_interface)

   2.2. [根据部门id获取](#unitId)

   2.3. [根据用户id获取](#userId)

----



- ## 一.获取课程资源接口<span id="kc_interface"/>

  - #### 请求URL

    http://ip:port/nc/api/resourceList

  - #### 请求参数

    - 必填

    > accessToken

    - 选填

    > pageIndex (分页页码参数-正整数)
    >
    > pageSize(分页页容量参数-正整数)

  - #### 请求方式

    - GET

  - #### 请求头参数

    - Content-Type=application/json

  - ####  返回类型

    - JSON类型

  - ####  返回参数说明

    |   参数名    |  类型  | 必填 |          说明          |
    | :---------: | :----: | :--: | :--------------------: |
    |     id      | String |  是  |         资源id         |
    |    type     |  int   |  是  | 资源类型 1课程 2专题班 |
    | state_value | String |  是  |  资源状态1启用 0 停用  |
    | state_text  | String |  是  |      资源状态文字      |
    |    title    | String |  是  |        资源名称        |
    |  abstract   | String |  是  |          简介          |
    |     url     | string |  是  |        资源地址        |
    | courseHour  | double |  否  |        资源课时        |
    | publishTime |  long  |  否  |        发布时间        |
    |  coverPath  | String |  否  |    资源封面，全路径    |

- #### 数据返回分支情况
  
  - 正常请求主分支(检索成功)
  
    ```json
    {
        "resourceList": [
            {
                "id": "00208a0b-1bbf-48dc-a957-27fc63b88068",
                "type": 1,
                "title": "科学应对压力，维护身心健康（下）",
                "url": "http://localhost:9081/dsf5/page.html#/pc/nc/pagecourse/coursePlayer?id=00208a0b-1bbf-48dc-a957-27fc63b88068",
                "courseHour": 1.0,
                "publishTime": 1517536282000,
                "coverPath": "https://xxb.e-celap.com/dsfa/upload/2018/02/img/coursewarePhoto/d0dc6403-f8c6-4711-8a0f-5d6573db7bc1.jpg",
                "state_value": "1",
                "state_text": "启用",
                "abstract": "世界卫生组织调查指出，人类疾病70%至80%的原因来自于压力与应急。压力是导致各类身心疾病的主要原因，而我们每个人每天都可能遇到各种各样、来自方方面面的压力。在处理来自于方方面面压力的同时，我们的身体也可能出现一些问题。\n该课程介绍了如何调节压力。首先，学会自我觉察。另外还有一种最重要的方法——腹式呼吸技术。"
            },
            {
                "id": "002ac6bf61ba42af8d1ea116621cc3a3",
                "type": 1,
                "title": "中国DT城市智能服务指数研究报告",
                "url": "http://localhost:9081/dsf5/page.html#/pc/nc/pagecourse/coursePlayer?id=002ac6bf61ba42af8d1ea116621cc3a3",
                "courseHour": 0.5,
                "publishTime": 1584954496000,
                "coverPath": "http://xuetang.dreamdt.cn/dsfa/upload/files/20200323/1ca9bca6b418436fba01f0670ea05844.png",
                "state_value": "0",
                "state_text": "未启用",
                "abstract": null
            }
        ]
    }
    ```
  
  - 异常请求分支(检索失败)
  
    ```json
      {
      	"resourceList":[]	
      }
    ```
  
    

-----







- ##  二.获取学习记录接口<span id="xxjl_interface" />

1. ###  根据部门id 获取部门下人员学习记录<span id="unitId" />

   - #### 请求URL

     http://ip:port/nc/api/xxjlByUnitId

   - #### 请求参数

     - 必填

     > accessToken

     > unitid (企业部门id)
     >
     > ds_update_time (记录的最早更新时间)

     - 选填

     > courseId (课程id)

   - #### 请求方式

     - GET

   - #### 请求头参数

     - Content-Type=application/json

   - #### 返回类型

     - JSON类型

   - #### 返回参数说明

     |     参数名     |  类型  | 必填 |            描述            |
     | :------------: | :----: | :--: | :------------------------: |
     |    unitCode    | String |  是  |          企业编码          |
     |     userId     | String |  是  |        用户唯一标识        |
     |    userName    | String |  是  |          用户姓名          |
     |    courseId    | String |  是  |           课程ID           |
     |     state      |  int   |  是  | 学习状态(0-未完成,1已完成) |
     | finished_time  |  long  |  否  |          完成时间          |
     | ds_update_time |  long  |  是  |     数据记录的更新时间     |
     | ds_create_time |  long  |  是  |     数据记录的开始时间     |
     |   courseHour   | double |  否  |          课程学时          |

   - 数据返回分支情况

     - 检索成功案例

     ```json
     {
         "progress":
         [
             {"unitCode":"7034960a8359488fb388bf9b8fde0e8c",
              "userId":"efc2613dda10473486a0f662d8d4933c",
              "userName":"任2",
              "courseId":"c459774e325640288ab6c5312ee1ad80",
              "state":1,
              "courseHour":null,
              "finished_time":null,
              "ds_update_time":1625797580000,
              "ds_create_time":1625796089000
             },
             {
                 "unitCode":"7034960a8359488fb388bf9b8fde0e8c",
                 "userId":"5d4fc5dd0d8c44a6b6a86715d8b19835",
                 "userName":"吕媛媛",
                 "courseId":"2894c4ba1f5040c780fc15fd157cad20",
                 "state":0,
                 "courseHour":null,
                 "finished_time":null,
                 "ds_update_time":1626686052000,
                 "ds_create_time":1625564435000
             }
         ]
     }
     ```

     - 检索失败案例

     ```json
     {
         "progress":[]
     }
     ```

     

2. ### 根据用户id获取个人学习记录<span id="userId">

    - #### 请求URL

      http://ip:port/nc/api/xxjlByUserId

    - #### 请求参数

      - 必填

      > accessToken
    
      > userId(用户id)
      >
      > ds_update_time (记录的最早更新时间)

      - 选填

      > courseId (课程id)

    - #### 请求方式

      - GET

    - #### 请求头参数

      - Content-Type=application/json

    - #### 返回类型

      - JSON类型

    - #### 返回参数说明
    
      |     参数名     |  类型  | 必填 |            描述            |
      | :------------: | :----: | :--: | :------------------------: |
      |    unitCode    | String |  是  |          企业编码          |
      |     userId     | String |  是  |        用户唯一标识        |
      |    userName    | String |  是  |          用户姓名          |
      |    courseId    | String |  是  |           课程ID           |
      |     state      |  int   |  是  | 学习状态(0-未完成,1已完成) |
      | finished_time  |  long  |  否  |          完成时间          |
      | ds_update_time |  long  |  是  |     数据记录的更新时间     |
      | ds_create_time |  long  |  是  |     数据记录的开始时间     |
      |   courseHour   | double |  否  |          课程学时          |

    - 数据返回分支情况

      - 检索成功案例
    
      ```json
      {
          "progress":
          [
              {
                  "unitCode":"7034960a8359488fb388bf9b8fde0e8c",
                  "userId":"efc2613dda10473486a0f662d8d4933c",
                  "userName":"任2",
                  "courseId":"c459774e325640288ab6c5312ee1ad80",
                  "state":1,
                  "courseHour":null,
                  "finished_time":null,
                  "ds_update_time":1625797580000,
                  "ds_create_time":1625796089000
              }
          ]
      }
      ```
      
      - 检索失败案例
      
      ```json
      {
          "progress":[]
      }
      ```

