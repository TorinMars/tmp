# 平台接口需求说明

## erp_chapter_class表

### 自定义接口

1. 获取一个时间段内，有行课班级的辅导老师数据，一个辅导老师一个学段只有一条数据

* 请求地址

  ```
  getInClassTutorDataByPartMode
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
| start | 开始时间 | long|
| end | 结束时间 | long|
| partMode | 学段 | String|

* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":[
          {			//返回数据详情
              "tutorId":"String",	//辅导老师id
              "tutorName":"String",	//辅导老师姓名
              "monthClassNum":"Integer",	//当月带班量
          }
      ]
  }
  ```

2. 获取一个当月行课班级的已行课次数据，每个辅导班课次一条数据

* 请求地址

  ```
  getSnapshotClassChapterInfo
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
| tutorId | 辅导班id |  String |
| testUsers | 需要排除的学生id | String[] |

* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":[
          {			//返回数据详情
              "id":"String",	//ID
              "classSnapshotId":"String",	//辅导班快照表主键
              "classId":"String",	//班级id
              "className":"String",	//班级名称
              "chapterId":"String",	//课次id
              "chapterName":"String",	//课次名称
              "chapterStartTime":"LocalDateTime",	//课次开始时间
              "chapterEndTime":"LocalDateTime",	//课次结束时间
              "isPublishHomework":"Integer",	//发布状态（0.未发布；1.已发布；2.取消发布）
              "attendanceNum":"Integer",	//出勤人数
              "noAttendanceNum":"Integer",	//未出勤人数
              "noAttendancePlaybackNum":"Integer",	//未出勤看回放人数
              "shouldAttendanceNum":"Integer",	//应出勤人数
              "submitHomeworkNum":"Integer",	//已提交作业人数
              "noSubmitHomeworkNum":"Integer",	//未提交作业人数
              "shouldSubmitHomeworkNum":"Integer",	//应提交作业人数
              "correctHomeworkNum":"Integer",	//已批改份数
              "attendanceRate":"Double",	//出勤率
              "finishClassRate":"Double",	//完课率
              "submitHomeworkRate":"Double"	//作业提交率
          }
      ]
  }
  ```

  

3. 获取一个时间段内，一个已行课班级的已行课次数据

* 请求地址

  ```
  getSnapshotClassChapterNum
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  | tutorId | 辅导班id | String|
| start | 开始时间 | long|
| end | 结束时间 | long|
| testUsers | 需要排除的学生id | String[]|

* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":[
          "Long",...	//课次数据
      ]
  }
  ```

  

4. 查询一个老师当月带的所有辅导班信息,每个辅导班都是一条数据

* 请求地址

  ```
  getTutorClassInfoDataByPartMode
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  | tutorId | 辅导班id | String|
| partMode | 学段 | String|
  | start | 开始时间 | long|
| end | 结束时间 | long|
| testUsers | 需要排除的学生id | String[]|

* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":[
          {
              "id":"String",	//ID
              "tutorSnapshotId":"String",	//辅导老师月度绩效快照表主键
              "classId":"String",	//班级id
              "className":"String",	//班级名称
              "teacherId":"String",	//主讲老师id
              "teacherName":"String",	//主讲老师姓名
              "chapterNums":"Integer",	//辅导班课次总数
              "inClassNum":"Integer",	//正常上课人数
              "attendanceNum":"Integer",	//出勤人数
              "noAttendanceNum":"Integer",	//未出勤人数
              "noAttendancePlaybackNum":"Integer",	//未出勤看回放人数
              "shouldAttendanceNum":"Integer",	//应出勤人数
              "submitHomeworkNum":"Integer",	//已提交作业人数
              "noSubmitHomeworkNum":"Integer",	//未提交作业人数
              "shouldSubmitHomeworkNum":"Integer",	//应提交作业人数
              "avgAttendanceRate":"Double",	//平均出勤率
              "avgFinishClassRate":"Double",	//平均完课率
              "avgSubmitHomeworkRate":"Double",	//平均作业提交率
          }
      ]
  }
  
  ```

  

5. 根据一个辅导班Id获取课次数据

* 请求地址

  ```
  getChapterMonitorListByClassID
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  |classId|辅导班ID|String|

* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":[
          {
              "chapterClassId":"String",	//班级课次ID
              "chapterId":"String",	//课次ID
              "chapterName":"String",	//课次名称
              "jobPublished":"String",	//是否已发布作业:0否,1是
              "attendanceRate":"String",	//出勤率
              "attendanceNum":"String",	//出勤人数
              "noAttendanceNum":"String",	//未出勤人数
              "shouldAttendanceNum":"String",	//应出勤人数
              "finishClassRate":"String",	//完课率
              "noAttendancePlaybackNum":"String",	//未出勤看回放人次
              "submitHomeworkRate":"String",	//作业提交率
              "shouldSubmitHomeworkNum":"String",	//应提交作业份数
              "submitHomeworkNum":"String",	//实提交作业份数
              "correctHomeworkNum":"String",	//已批改份数
              "endTime":"LocalDateTime",	//结束时间 yyyy-MM-dd HH:mm:s
              "startTime":"LocalDateTime",	//开始时间 yyyy-MM-dd HH:mm:s
          }
      ]
  }
  
  
  ```

  

6. 获取一个辅导班的课次信息

* 请求地址

  ```
  getChapterBytutorId
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  |classId|辅导班ID|String|

* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":[
          {
              "chapterId":"String",	//班级课次ID
              "chapterName":"String",	//班级课次名称
              "startTime":"LocalDateTime",	//开始时间
              "endTime":"LocalDateTime",	//结束时间
              "chapterClassId":"String",	//章节班级ID
          }
      ]
  }
  
  ```

7. 获取班级课程信息(与6重复无需开发)

* 请求地址

  ```
  getChaptInfoByClassId
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  |classId|辅导班ID|String|

* 返回参数

  ```json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":[
          {
              "chapterId":"String",	//班级课次ID
              "chapterName":"String",	//班级课次名称
              "startTime":"LocalDateTime",	//开始时间
              "endTime":"LocalDateTime",	//结束时间
              "chapterClassId":"String",	//章节班级ID
          }
      ]
  }
  ```

  

8. 根据主讲班和课次获取所有辅导班的直播教室ID

* 请求地址
  ```
  queryTutorRoomId
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  | mainClassId | 主讲班ID |Long|
  | chapterId | 课次ID |Long|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":[
          {
              "classId":"String",	//课程ID
              "zbRoomId":"String",	//直播房间ID
          }
      ]
  }
  
  ```

9. 通过主讲课ID获取课次信息

* 请求地址
  ```
  getChapterUseHsc
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  | classIdMain| 主讲课ID|Long|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":[
          {
              "chapterId":"String",	//课次ID
              "chapterName":"String",	//课次名称
              "endTime":"Long",	//结束时间
              "startTime":"Long",	//开始时间
          }
      ]
  }
  
  ```

10. 通过章节课程ID获取章节课程信息

* 请求地址
  ```
  getChapterClass
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  | chapterClassId| 章节课程ID|Long|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":[
          {
          	"chapterClassId":"Long",
            "chapterClassIdMain":"Long",
            "chapterId":"Long",
            "chapterName":"String",
            "courseId":"Long",
            "classId":"Long",
            "status":"Integer",
            "endTime":"Long",
            "startTime":"Long",
            "teacherId":"Long",
            "teacherName":"String",
            "assistantId":"Long",
            "assistantName":"String",
            "playbackUrl":"String",
            "zbClassId":"String",
            "zbRoomId":"String",
            "classStatus":"Integer",
            "serveType":"Integer",
            "createUid":"Long",
            "modifyUid":"Long",
            "createTime":"Long",
            "modifyTime":"Long",
            "settlementStatus":"Integer",
          }
      ]
  }
  
  ```

11. 通过课程ID和截止时间获取课程数量

* 请求地址
  ```
  countClassOrder
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  | classId| 课程ID|Long|
  | endTime| 截止时间|Long|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": "Integer"
  }
  
  ```
  

12. 查询当前课次下应出勤学生id集合

* 请求地址
  ```
  listStudentIdByClassId
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  |chapterClassId|章节课程ID|Long|

* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":[
        "Long"	//学生ID集合
      ]
  }
  
  ```


13. 通过课程ID获取课程下的所有学生信息

* 请求地址
  ```
  listStudentMobileByClassId
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  |classId|课程ID|Long|

* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":[
        {
          	"studentStudyId":"String",
            "studentId":"Long",
            "stuMobil":"String",
            "stuNickname":"String",
            "stuName":"String",
        }
      ]
  }
  
  ```


14. 查询需要同步回放记录的课次

* 请求地址
  ```
  selectRoomIds
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  |pageIndex|页码偏移量|Integer|
  |pageSize|页码显示数量|Integer|

* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":[
        "Long"	//课次ID
      ]
  }
  
  ```

15. 根据学生id 主讲课次id 查询当前学生所在辅导班课次id

* 请求地址
  ```
  getRealChapterClassId
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  |studentId|学生ID|String|
  |chapterClassIdMain|主讲课次ID|String|

* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":"Long"	//课次ID
  }
  ```

16. 根据辅导老师ID时间获取数量

* 请求地址
  ```
  countByAssisIdTime
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  |startTime|开始时间|Long|
  |endTime|结束时间|Long|
  |assistentId|辅导老师ID|Long|
  |status|状态信息|Integer|

* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":"Integer"	//数量
  }
  ```
  ![image-20200910104144553](https://tva1.sinaimg.cn/large/007S8ZIlly1gilcwdvyp7j31b208u76r.jpg)

### MabitisPlus通用接口

1. 通过queryWrapper查询一个课程课次信息`selectOne`
2. 通过ID查询一个课程课次信息`selectById`
3. 通过queryWrapper查询课程课次的数量`selectCount`
4. 通过queryWrapper查询课程课次的列表`selectList`

## erp_chapter表

### 自定义接口

无

### mybatisPlus通用接口

1. 通过ID查询一个课次信息 selectById

<img src="https://tva1.sinaimg.cn/large/007S8ZIlly1gild6zlajkj30o80demys.jpg" alt="image-20200910105158263" style="zoom:150%;" />

## erp_class表

### 自定义接口

1. 分页获取课程监控信息

* 请求地址
  ```
  getClassMonitorData
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  | page | 当前页 | Integer |
  | pageSize | 单页数量 | Integer |
  | classStatus | 班级状态 | String |
| className | 班级名称 | String |
| classTeacher | 主讲老师 | String |
| tutorTeacher | 辅导老师 | String |
| partMode | 学段 | String |
| gradeModes | 年级 | List<String> |
| subjectMode | 学科 | String |
| courseMode | 课程类型 | String |
| quarterMode | 学期 | String |
| year | 年份 | String |
| beginTime | 上课日期开始 | LocalDateTime |
| endTime | 上课日期结束 | LocalDateTime |
| beginTimeStamp | 上课日期开始 | Long |
| endTimeStamp | 上课日期结束 | Long |


* 返回参数 (Ipage对象)

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data":{
          "total":"Long",
          "size":"Long",
          "current":"Long",
          "records":[{
                "classId":"String",	//辅导班ID
                "mastercId":"String",	//主讲班ID
                "className":"String",	//班级名称
                "classTeacher":"String",	//主讲老师
                "tutorTeacher":"String",	//辅导老师
                "attendanceRate":"String",	//出勤率
                "attendanceNum":"String",	//出勤人数
                "noAttendanceNum":"String",	//未出勤人数
                "shouldAttendanceNum":"String",	//应出勤人数
                "finishClassRate":"String",	//完课率
                "noAttendancePlaybackNum":"String",	//未出勤看回放人次
                "submitHomeworkRate":"String",	//作业提交率
                "shouldSubmitHomeworkNum":"String",	//应提交作业份数
                "submitHomeworkNum":"String",	//实提交作业份数
                "beginTime":"LocalDateTime",	//上课日期开始
                "endTime":"LocalDateTime",	//上课日期结束
                "partMode":"String",	//学段
                "subjectMode":"String",	//学科
                "gradeModes":"List<String>",	//年级
                "gradeModeString":"String",	//年级模式
                "tutorNum":"String",	//辅导班人数
                "masterNum":"String",	//主讲班人数
                "classStatus":"String",	//班级状态
                "chapterNum":"String",	//课次数量
          }]
      }
  }
  ```
  
2. 获取一个主讲班下所有学员数量

* 请求地址
  ```
  getMasterClassStudentNum
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  | mastercId | 主讲班ID | String|
| testUsers | 测试学生列表 | String[]|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": "Integer"	//学员数量
  }
  ```
  
3. 获取一个辅导班下所有学员

* 请求地址
  ```
  getTutorClassStudentNum
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
| tutorId | 辅导班ID | String |
| testUsers | 测试学生列表 | String[] |


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": "Integer"	//学员数量
  }
  ```

4. 获取一个辅导班的出勤数量

* 请求地址
  ```
  getClassPlaybackNum
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
| tutorId | 辅导班ID | String |
| testUsers | 测试学生列表 | String[] |


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": "Integer"	//出勤数量
  }
  ```

5. 获取一个辅导班的未出勤看回放情况

* 请求地址
  ```
  getClassAttendanceNum
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
| tutorId | 辅导班ID | String |
| testUsers | 测试学生列表 | String[] |


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": {
      	"shouldAttendanceNum":"Integer",	//应出勤数
      	"attendanceNum":"Integer",	//观看量
      }
  }
  ```

6. 获取班级相关信息

* 请求地址
  ```
  getClassInfo
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
| chapterId | 课次ID | String |
| classId | 班级ID | String[] |


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": {
      	"partMode":"String", 	//学段code
      	"quarterMode":"String", 	//学期code
      	"subjectMode":"String", 	//学科code
      	"gradeMode":"String", 	//年级code
      }
  }
  ```

7. 获取主讲班信息

* 请求地址
  ```
  masterClassQuery
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
|pageSize|页数|Integer|
|pageNo|页码|Integer|
|className|主讲课课程名称|String|
|teacherName|主讲老师名称|String|
|subjectMode|学科|String|
|partMode|学段|String|
|gradeModes|年级|String|
|courseMode|课程类型|String|
|startTime|开始时间|Long|
|endTime|结束时间|Long|
|quarterMode|学期|String|
|classStatus|上课状态|Integer|


* 返回参数 (Ipage对象)

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": [{
      	"classId":"String",	//主讲班ID
      	"className":"String",	//课程名称
      	"teacherId":"String",	//老师id
      	"courseMode":"String",	//课程code
      	"startTime":"Long",	//开始时间
      	"endTime":"Long",	//结束时间
      	"quarterMode":"String",	//学期
      	"partMode":"String",	//学段
      	"gradeMode":"String",	//年级
      	"gradeModes":"String",	//年级(多个)
      	"subjectMode":"String",	//学科
      	"userLogin":"String",	//用户
      }]
  }
  ```

8. 获取主讲班查询记录数

* 请求地址
  ```
  countMasterClassQuery
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
|pageSize|页数|Integer|
|pageNo|页码|Integer|
|className|主讲课课程名称|String|
|teacherName|主讲老师名称|String|
|subjectMode|学科|String|
|partMode|学段|String|
|gradeModes|年级|String|
|courseMode|课程类型|String|
|startTime|开始时间|Long|
|endTime|结束时间|Long|
|quarterMode|学期|String|
|classStatus|上课状态|Integer|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": "Integer"
  }
  ```


9. 根据主讲班id获取所有的辅导班信息

* 请求地址
  ```
  countMasterClassQuery
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
|classId|课程ID|String|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": [{
      	"assistantId":"String",	//辅导老师ID
      	"assistantName":"String",	//辅导老师名称
      	"classId":"String",	//班级ID
      }]
  }
  ```

10. 获取主讲班信息

* 请求地址
  ```
  getMatercList
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
|classId|班级ID|String|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": [{
        "mastercId":"String",	\\主讲班id
        "className":"String",	\\班级名称
        "courseId":"String",	\\课程id  非chapterId
        "mastercTeacher":"String",	\\主讲老师
        "mastercTeacherName":"String",	\\主讲老师姓名
        "classStartTime":"LocalDateTime",	\\班级开始时间
        "classEndTime":"LocalDateTime",	\\班级结束时间
        "year":"Integer",	\\年份
      	"grade":"String",	\\年级
      	"term":"String",	\\学期
      	"termCode":"String",	\\学期
      	"termName":"String",	\\学期
      	"partMode":"String",	\\学段
      	"partModeCode":"String",	\\学段
      	"partModeName":"String",	\\学段
      	"subject":"String",	\\学科
      	"subjectCode":"String",	\\学科
      	"subjectName":"String",	\\学科
      	"courseType":"String",	\\课程类型
      	"courseTypeCode":"String",	\\课程类型
      	"courseTypeName":"String",	\\课程类型
        "grades":"List<String>",	\\grade转换的集合数组
        "courseList":"List<CourseDto>",	\\课次数组
        "classStatus":"Integer",	\\班级状态 0未开课 1开课中 2已结课
      }]
  }
  ```


11. 获取课次列表

* 请求地址
  ```
  getCourses
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
|classId|班级ID|String|
|courseId|课程ID|String|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": [{
        "chapterId":"String",	\\课次id
        "chapterName":"String",	\\课次名称
        "chapterStatus":"Integer",	\\课次状态
        "chapterSort":"Integer",	\\课次序号
        "chapterStartTime":"LocalDateTime",	\\课次开始时间
        "chapterEndTime":"LocalDateTime",	\\课次结束时间
      }]
  }
  ```

12. 根据辅导班ID获取辅导班信息

* 请求地址
  ```
  getTutorClass
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
|tutorialcId|辅导班ID|String|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": [{
        "mastercId":"String",	\\主讲班id
        "tutorialcId":"String",	\\辅导班id
        "tutorId":"String",	\\辅导老师id
        "tutorName":"String",	\\辅导老师姓名
      }]
  }
  ```

13. hcs同步班级,获取班级信息

* 请求地址
  ```
  getClassModelVO
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
|classId|班级ID|String|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": [{
        "classId":"Long",
        "className":"String",
        "teacherId":"Long",
        "courseMode":"String",
        "startTime":"Long",
        "endTime":"Long",
        "quarterMode":"String",
        "partMode":"Integer",
        "gradeMode":"String",
        "gradeModes":"String",
        "subjectMode":"String",
        "teacherName":"String",
        "classIdMain":"String",
      }]
  }
  ```

14. 获取课程辅导老师信息

* 请求地址
  ```
  getClassModelByClassIdMainUseHsc
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
|classIdMain|主讲课程ID|Long|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": [{
        "assistantName":"String",	//辅导老师名称
        "assistantId":"String",	//辅导老师ID
        "classId":"String",	//辅导班ID
      }]
  }
  ```



### MabitisPlus通用接口

1. 通过queryWrapper查询一个班级信息`selectOne`
2. 通过ID查询一个班级信息`selectById`
3. 通过queryWrapper查询班级的数量`selectCount`
4. 通过queryWrapper查询班级的列表`selectList`

## erp_class_student表

### 自定义接口


1. 获取一个辅导班，某个课次的未上课看直播数据

* 请求地址
  ```
  getSinglePlaybackNum
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  |tutorId|辅导班ID|String|
  |chapterClassId|班课ID|String|
  |testUsers|需要排除的学生ID|String[]|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": "Integer"
  }
  ```

2. 获取一个辅导班，某个课次的未上课看直播数据

* 请求地址
  ```
  getSinglePlaybackNum
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  |tutorId|辅导班ID|String|
  |chapterClassId|班课ID|String|
  |testUsers|需要排除的学生ID|String[]|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": {
      	"shouldAttendanceNum":"Integer",	//应到人数
      	"attendanceNum":"Integer",	//实际人数
      }
  }
  ```

3. 获取辅导班下的所有学生

* 请求地址
  ```
  getSinglePlaybackNum
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  |classId|班级ID|String|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": [{
      	"classId":"Integer",	//辅导班ID
      	"studentId":"Integer",	//学生ID
      	"studentName":"Integer",	//学生名
      	"wxNamw":"Integer",	//微信名
      	"mobile":"Integer",	//手机号
      	"status":"Integer",	//学生上课状态 1.正常上课2.已转班3.已退费4.退款中
      	"avatar":"Integer",	//学生头像
      	"studentNick":"Integer",	//学生昵称
      }]
  }
  ```
  
4. 获取辅导班下的所有学生

* 请求地址
  ```
  getSinglePlaybackNum
  ```

* 请求参数

  | 请求参数名 | 请求中文名 | 请求类型 |
  | ---------- | ---------- | -------- |
  |classId|班级ID|String|
  |status|学生上课状态 1.正常上课2.已转班3.已退费4.退款中|String|
  |testUser|需要忽略的学生ID|String[]|


* 返回参数

  ``` json
  {
      "code":"Integer",	//返回编码
      "message":"String", //返回消息
      "data": "Integer", //数量
  }
  ```
  
  ![image-20200910171443793](https://tva1.sinaimg.cn/large/007S8ZIlly1gilo9an94aj313o0ae0v6.jpg)

### MabitisPlus通用接口

1. 通过ID查询一个课程学生信息`selectById`
2. 通过queryWrapper查询一个课程学生信息`selectOne`
3. 通过queryWrapper查询课程学生的数量`selectCount`
4. 通过queryWrapper查询课程学生的列表`selectList`

## erp_course表

### 自定义接口

无

### MabitisPlus通用接口

1. 通过ID查询一个课程信息`selectById`
2. 通过queryWrapper查询一个课程信息`selectOne`
3. 通过queryWrapper查询课程的数量`selectCount`
4. 通过queryWrapper查询课程的列表`selectList`

## erp_student表

### 自定义接口

无

### MabitisPlus通用接口

1. 通过ID查询一个学生信息`selectById`
2. 通过queryWrapper查询一个学生信息`selectOne`
3. 通过queryWrapper查询学生的数量`selectCount`
4. 通过queryWrapper查询学生的列表`selectList`
