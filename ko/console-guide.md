## Search > Cloud Search > 콘솔 사용 가이드

## 문서 설명
* 문서 내의 호스트명 "alpha-api-search.cloud.toast.com"는 사용자별로 다를 수 있습니다.
* 문서 내의 앱키 "bJsVUwrftmEl4K7D"는 사용자별로 다를 수 있습니다.

## 상품 활성화
* Cloud Search 서비스를 활성화하기 위해서 Console로 이동합니다.
* 활성화 방법
    ![](http://static.toastoven.net/prod_search/product-use-02-20180724.png)
    1. "서비스 선택"을 클릭합니다.
    2. "Cloud Search"를 클릭해서 서비스를 활성화합니다.
   <br><br>
* 활성화 확인
    ![](http://static.toastoven.net/prod_search/product-use-03-20180724.png)
    1. "Search" 클릭합니다.
    2. "Cloud Search"가 노출되면 활성화된 것입니다.

## 기본 사용법

### 1. 서비스 생성
* 서비스 생성 방법
    ![](http://static.toastoven.net/prod_search/domain_create_procedure.png?)
    1. "서비스 생성" 버튼을 클릭합니다.
    2. 서비스 ID를 입력합니다.
        * 영어 소문자, 숫자 및 \_(underscore)와 -(dash)만 사용할 수 있습니다.
        * 숫자, \_(underscore), -(dash)로 시작할 수 없습니다.
        * 최소 두 글자 이상 가능합니다.
    3. "저장" 버튼을 클릭합니다.
    <br><br>
* 서비스 생성 결과
    ![](http://static.toastoven.net/prod_search/domain_create_result.png?)
    1. 생성된 서비스 ID(test)를 클릭합니다.

### 2. 필드 설정
* 필드 추가 방법
    ![](http://static.toastoven.net/prod_search/field_create_procedure-20190129.png)
    1. "필드 설정" 탭을 클릭합니다.
    2. "필드 추가" 버튼을 클릭합니다.
    3. 필드 이름을 입력합니다.
        * 영어 대소문자, 숫자 및 \_(underscore)와 -(dash)만 사용할 수 있습니다.
        * 숫자, \_(underscore), -(dash)로 시작할 수 없습니다.
        * 최소 두 글자 이상 가능합니다.
    4. "저장" 버튼을 클릭합니다.
    <br><br>
* 필드 삭제 방법
    ![](http://static.toastoven.net/prod_search/field_delete-1-20190129.png?)
    ![](http://static.toastoven.net/prod_search/field_delete-2-20190129.png?)
    ![](http://static.toastoven.net/prod_search/field_delete-3-20190129.png?)
    1. 삭제할 필드의 "삭제" 버튼을 클릭합니다.
    2. "저장" 버튼을 클릭합니다.
    3. "지금 수행" 버튼을 클릭합니다.
        * 재색인 중에는 문서 추가, 수정, 삭제가 안됩니다.
    <br><br>
* 필드 수정 방법
    * 필드 수정은 지원하지 않습니다. 삭제후 다시 추가해야 합니다.

### 3. 색인
* 색인할 파일 생성
    * 아래 예제와 같은 형식으로 색인 요청 파일을 생성합니다.
    * <span style="color:red">색인할 파일은 UTF-8로 생성해야 합니다.</span>
        * Windows 메모장에서 파일 저장시 인코딩을 UTF-8로 지정해서 저장합니다.
    * 예제에서는 data/documents.json 이름으로 생성했습니다.
    ```
    [
      {
        "action": "add",
        "id": "id-1",
        "fields": {
          "title": "[무료배송]나이키 슈즈 195종!!",
          "body": "명불허전 나이키 인기슈즈 괜히 잘 팔리는게 아니죠~~ 나이키 핫!슈즈 195종★ 하나쯤은 있어야 하지 않아??"
        }
      },
      {
        "action": "add",
        "id": "id-2",
        "fields": {
          "title": "[슈퍼특가]나이키 운동화 109종",
          "body": "단 7일만 이가격!  [슈퍼특가] 아디다스 슈즈 109종 모음전 망설이면 품~절~"
        }
      },
      {
        "action": "add",
        "id": "id-3",
        "fields": {
          "title": "[아디다스]신상운동화/슬리퍼 114종",
          "body": "[아디다스슈즈모음♥] 무/료/배/송 [아디다스]신상슬리퍼 /슈퍼스타 스탠스미스 /튜블라외 114종 득템기회!"
        }
      }
    ]
    ```
    * action
        * add : 해당 문서가 추가됩니다.
            * 기존에 동일한 id가 존재하면 업데이트 됩니다.
        * delete : 해당 문서가 삭제됩니다.
    * id
        * 문서의 고유한 ID입니다.
        * id의 타입은 문자열입니다.
    * 최대 파일 사이즈는 8Mb입니다.
        * 8Mb 이상의 데이터는 여러 개로 나누어서 색인해야 합니다.
    <br><br>
* 색인 방법
    ![](http://static.toastoven.net/prod_search/indexing_procedure_01.png)
    ![](http://static.toastoven.net/prod_search/indexing_procedure-02-20190129.png)
    1. "색인" 탭을 클릭합니다.
    2. "파일 선택" 버튼을 클릭합니다.
    3. 색인할 파일을 선택합니다.
    4. "열기" 버튼을 클릭합니다.  
    5. 색인 명령어가 REST API로 출력됩니다.
        * Rest API를 이용해서 검색 서비스를 연동하시면 됩니다.
    6. "색인" 버튼을 클릭합니다.
    7. 색인 결과를 확인할 수 있습니다.
    <br><br>
* Rest API
    * 아래와 같이 REST API를 사용 가능합니다.
    * 색인 API
        * Request
            * 파일 업로드 방식
                ```
                curl -XPOST 'https://alpha-api-search.cloud.toast.com/indexing/v1.0/appkeys/bJsVUwrftmEl4K7D/serviceids/test/indexing' -H 'Content-Type:multipart/form-data; charset=UTF-8' -F 'file=@documents.json'
                ```
            * Payload 방식
                ```
                curl -XPOST 'https://alpha-api-search.cloud.toast.com/indexing/v1.0/appkeys/bJsVUwrftmEl4K7D/serviceids/test/indexing' -H 'Content-Type:application/json; charset=UTF-8' -d '
                [
                  {
                    "action": "add",
                    "id": "id-1",
                    "fields": {
                      "title": "[무료배송]나이키 슈즈 195종!!",
                      "body": "명불허전 나이키 인기슈즈 괜히 잘 팔리는게 아니죠~~ 나이키 핫!슈즈 195종★ 하나쯤은 있어야 하지 않아??"
                    }
                  },
                  {
                    "action": "add",
                    "id": "id-2",
                    "fields": {
                      "title": "[슈퍼특가]나이키 운동화 109종",
                      "body": "단 7일만 이가격!  [슈퍼특가] 아디다스 슈즈 109종 모음전 망설이면 품~절~"
                    }
                  }
                ]'
                ```
        * Response
            ```        
            {
              "id" : 1
            }
            ```
    * 색인 결과 확인 API
        * Request
            ```
            curl -i -XGET 'https://alpha-api-search.cloud.toast.com/indexing/v1.0/appkeys/bJsVUwrftmEl4K7D/serviceids/test/indexing_log?id=1'
            ```  
            * id 1은 위의 색인 API Response 의 id입니다.
        * Response
            ```
            {
              "request_time" : "2017-10-23T12:36:43",
              "file_name" : "documents.json",
              "file_size" : 1185,
              "status" : 4
            }
            ```
            * status
                * 1 : 대기 중
                * 2 : 무시됨 (필드 설정 변경 이전의 색인 요청은 무시됨)
                * 3 : 진행 중
                * 4 : 성공
                * 5 : 실패

### 4. 검색
* 검색 방법
    ![](http://static.toastoven.net/prod_search/basic-search-20190129.png)
    1. "검색" 탭을 클릭합니다.
    2. 검색할 필드명을 체크합니다.
    3. 검색할 필드별 가중치를 설정합니다.
        * 0.0 ~ 1.0 값을 설정합니다.
    4. 검색 결과에 출력할 필드를 체크합니다.
    5. 검색 결과 길이를 설정합니다.
    6. 강조(Highlight) pre 태그를 설정합니다.
    7. 강조(Highlight) post 태그를 설정합니다.
    8. 검색 결과에서 출력할 시작 순위를 지정합니다.
        * "1"로 설정하면 1등부터 출력되고, "10"으로 설정하면 10등부터 출력됩니다.
    9. 검색 결과 개수를 지정합니다.
        * "5"로 설정하면 5개 출력되고, "10"으로 설정하면 10개 출력됩니다.
    10. 검색 연산자를 선택합니다.
    11. 검색할 단어를 입력합니다.
    12. 검색 아이콘을 클릭합니다.
    13. 2 ~ 11번까지 설정한 내용이 REST API로 출력됩니다.
        * Rest API를 이용해서 검색 서비스를 연동하시면 됩니다.
    14. 검색 결과가 출력됩니다.
    <br><br>
* Rest API
    * 아래와 같이 REST API를 사용 가능합니다.
    * Request
        ```
        curl -G -XGET 'https://alpha-api-search.cloud.toast.com/search/v1.0/appkeys/bJsVUwrftmEl4K7D/serviceids/test/search?start=1&size=10&q_option=and,body*1.0,title*1.0&return=&passage.body=180&passage.title=180' --data-urlencode q='나이키 운동화' --data-urlencode highlight='<b>,</b>'
        ```
    * Response
        ```
        {
          "message" : {
              "meta" : {
                "timezone" : "+09:00"
              },
              "result" : {
                "status" : {
                "code" : 200,
                "message" : "OK"
              },
              "query" : "나이키 운동화",
              "start" : 1,
              "itemCount" : 1,
              "total" : 1,
              "itemList" : {
                "item" : [
                {
                  "_RELEVANCE" : 0.07575758,
                  "_RANK" : 1,
                  "_ID" : "id-2",
                  "body" : "단 7일만 이가격!  [슈퍼특가] 아디다스 슈즈 109종 모음전 망설이품~절~",
                  "title" : "[슈퍼특가]<b>나이키</b> <b>운동화</b> 109종"
                }
                ]
              }
            }
          }
        }
        ```
### 5. 통계
* 통계 화면
    ![](http://static.toastoven.net/prod_search/stats-20190129.png)
    1. "통계" 탭을 클릭합니다.
    2. "전체 질의수" 또는 "결과 없는 질의수"를 선택합니다.
    3. 시작 날짜를 입력합니다.
    4. 종료 날짜를 입력합니다.
    5. "조회" 버튼을 클릭하면 통계 그래프가 출력됩니다.
    6. "데이터 다운로드"를 클릭하면 질의별 통계 데이터가 다운로드됩니다.
    7. "전체 문서수" 또는 "전체 색인 사이즈"를 선택합니다.
    8. 시작 날짜를 입력합니다.
    9. 종료 날짜를 입력합니다.
    10. "조회" 버튼을 클릭하면 통계 그래프가 출력됩니다.
* Rest API
    * Request
        ```
        curl -i -XGET 'http://alpha-api-search.cloud.toast.com/stats/v1.0/appkeys/bJsVUwrftmEl4K7D/serviceids/test/stats?kind=total_query_count&date=2019-01-08'
        ```
        * kind
            * total_query_count : 전체 질의수
            * no_result_query_count : 검색 결과 없는 질의수
        * date : 조회할 날짜
    * Response
        ````
        [ [ "나이키", 8 ], [ "아디다스", 4 ] ]
        ````
        * 질의수 3 이상만 조회됩니다.

### 6. ACL
* 색인 및 검색 REST API를 호출할 수 있는 장비의 IP를 제한할 수 있습니다.
    * <span style="color:red">다른 사람이 데이터를 삭제할 수 있으므로 색인 ACL은 반드시 설정해 주세요.</span>
    * 콘솔에서 테스트하는 경우 ACL 설정과 관련 없습니다.		
* ACL 설정 방법
    ![](http://static.toastoven.net/prod_search/acl_procedure-20190129.png)
    1. "ACL" 탭을 클릭합니다.
    2. 색인 요청은 IP 주소가 202.179.177.21 인 경우만 색인이 가능하도록 설정한 예제입니다.
    3. 검색 요청은 모든 IP에서 가능하도록 설정한 예제입니다.
    4. 질의 통계 데이터 다운로드 요청는 모든 IP에서 가능하도록 설정한 예제입니다.
    5. "저장" 버튼을 클릭합니다.

## 기능 가이드

### 필터링
* 필드 설정
    ![](http://static.toastoven.net/prod_search/filtering-field-20190129.png)
* 색인
    * 테스트를 위해 아래 데이터를 색인합니다.
    ```
    [
    {
      "action": "add",
      "id": "id-1",
      "fields": {
        "name" : "나이키 에어맥스",
        "category" : 1
      }
    },
    {
      "action": "add",
      "id": "id-2",
      "fields": {
        "name" : "나이키 샤이엔 솔리드",
        "category" : 2
      }
    }
    ]
    ```
    <br>
* 검색
    ![](http://static.toastoven.net/prod_search/filtering-search-20190129.png)
    1. "category"가 "1"인 문서만 검색됩니다.
    <br><br>
* 필터링 값 입력 방법
    * 단일 값 필터링
        * 예제) category=1
            * category == 1
    * or 필터링
        * 예제) category=1|2
            * category == 1 or category == 2
    * and 필터링
        * 예제) category=1&2
            * category == 1 and category == 2      
    * 범위 지정 필터링		
        * 예제) category=[1,2]
            * 1 <= category <= 2
        * 예제) category={1,2]      
            * 1 < category <= 2
        * 예제) category={,2]      
            * category <= 2
        * keyword, boolean, geo_point 타입은 범위 지정 필터링에 사용할 수 없습니다.
    * not 필터링
        * 예제) category=!1
            * category != 1
        * 예제) category=!1|2
            * category !=1 or category == 2
    * date 타입 필터링
        * filter='update=[2017-03-22T08:28:44,}'
            * 2017-03-22T08:28:44 <= update
        * filter='update=[,2018-10-02T15:26:28}'
            * update < 2018-10-02T15:26:28
        * filter='update=[2017-03-22T08:28:44,2018-10-02T15:26:28}'
            * 2017-03-22T08:28:44 <= update < 2018-10-02T15:26:28
    * keyword 타입 필터링
        * filter='dealer="DNC샵"|"위드쇼핑"'
            * keyword 타입은 큰따옴표 사용을 추천합니다.
* 여러 개의 필드 필터링
    * filter='category=1&brand=2'
        * category == 1 and brand == 2
    * filter='category=1|brand=2'
        * category == 1 or brand == 2
    * filter='(category=1&brand=2)|(category=3&brand=4)'
        * (category == 1 and brand == 2) or (category == 3 and brand == 4)

### 위경도(geolocation) 필터링
* 필드 설정
    ![](http://static.toastoven.net/prod_search/geolocation-field-20190129.png)
    1. 위경도를 입력할 필드 타입으로 "geo_point"를 선택합니다.
    <br><br>
* 색인
    * 테스트를 위해 아래 데이터를 색인합니다.
    ```
    [
    {
      "action": "add",
      "id": "id-1",
      "fields": {
        "name" : "에프엑스수학학원",
        "location" : [10.1, 10.1]
      }
    },
    {
      "action": "add",
      "id": "id-2",
      "fields": {
        "name" : "좋은나무 사고력수학학원",
        "location" : [10.3, 10.4]
      }
    },
    {
      "action": "add",
      "id": "id-3",
      "fields": {
        "name" : "수학의아침학원",
        "location" : [10.4, 10.3]
      }
    }
    ]
    ```
    * geo_point 타입에는 [{경도}, {위도}] 형식으로 값을 입력합니다.
    <br><br>
* 검색
    * 반경(circle) 필터링
        ![](http://static.toastoven.net/prod_search/geolocation-search-circle-20190129.png)
        1. 필터링 값을 입력합니다.
            * 형식 : [{경도},{위도}],{반경}
            * 예제 : [10.3,10.3],15km
                * 경도 10.3, 위도 10.3 중심으로 반경 15km 이내인 문서만 검색됩니다.
            * 반경 단위는 "km", "m", "cm"를 사용할 수 있습니다.
    <br><br>
    * 영역(polygon) 필터링
        ![](http://static.toastoven.net/prod_search/geolocation-search-polygon-20190129.png)
        1. 필터링 값을 입력합니다.
            * 형식 : [{경도 1},{위도 1}],[{경도 2},{위도 2}],[{경도 N},{위도 N}]
            * 예제 : [10.2,10.2],[10.3,10.5],[10.5,10.2]
            * 각 점들은 시계 방향으로 연결됩니다.
            * 연결된 다각형 내의 문서만 검색됩니다.

### 정렬
* 필드 설정
    ![](http://static.toastoven.net/prod_search/sorting-field-20190129.png)
* 색인
    * 테스트를 위해 아래 데이터를 색인합니다.
    ```
    [
    {
      "action": "add",
      "id": "id-1",
      "fields": {
        "name" : "나이키 에어맥스",
        "popular" : 10,
        "price" : 84180
      }
    },
    {
      "action": "add",
      "id": "id-2",
      "fields": {
        "name" : "나이키 에어줌",
        "popular" : 5,
        "price" : 97200
      }
    },
    {
      "action": "add",
      "id": "id-3",
      "fields": {
        "name" : "나이키 에어포스",
        "popular" : 5,
        "price" : 74680
      }
    }
    ]
    ```
    <br>
* 검색
    ![](http://static.toastoven.net/prod_search/sorting-search-20190129.png)
    1. 정렬 방식을 지정합니다.
        * "asc" : 올림차순 정렬
        * "desc" : 내림차순 정렬
    2. 정렬 순서를 지정합니다.
        * 위의 예제에서는 "popular"로 먼저 정렬합니다.
        * "popular"가 동일한 경우 "price"로 정렬합니다.    

### 요약
* 필드 설정
    ![](http://static.toastoven.net/prod_search/aggregation-field-20190129.png)
    * 색인이 체크된 필드만 요약 기능을 사용할 수 있습니다.
* 색인
    * 테스트를 위해 아래 데이터를 색인합니다.
    ```
    [
    {
      "action": "add",
      "id": "id-1",
      "fields": {
        "name" : "나이키 에어맥스",
        "category" : "신발"
      }
    },
    {
      "action": "add",
      "id": "id-2",
      "fields": {
        "name" : "나이키 에어줌",
        "category" : "신발"
      }
    },
    {
      "action": "add",
      "id": "id-3",
      "fields": {
        "name" : "나이키 스우시 반팔티",
        "category" : "의류"
      }
    }
    ]
    ```
    <br>
* 검색
    ![](http://static.toastoven.net/prod_search/aggregation-search-20190129.png)
    * 요약 사용 방법
        1. "category" 필드의 "요약"을 체크합니다.
            * 검색 결과와 함께 요약 정보가 출력됩니다.
            ```
            "summary": {
              "category": {
                "신발": 2,
                "의류": 1
              }
            }
            ```
            * "category"가 "신발"인 검색 결과가 2건, "의류"인 검색 결과가 1건이라는 의미입니다.
            <br>
    * 요약 가능한 타입
        * text 및 geo_point 타입은 요약 기능을 사용할 수 없습니다.

### 불리언 질의
* 필드 설정
    ![boolean_query-field-20190129](https://static.toastoven.net/prod_search/boolean_query-field-20190129.png)

* 색인
    * 테스트를 위해 아래 데이터를 색인합니다.
    ```
    [
    {
      "action": "add",
      "id": "id-1",
      "fields": {
        "title" : "나이키 신발"
      }
    },
    {
      "action": "add",
      "id": "id-2",
      "fields": {
        "title" : "나이키 슈즈"
      }
    },
    {
      "action": "add",
      "id": "id-3",
      "fields": {
        "title" : "나이키 가방"
      }
    }
    ]
    ```
    <br>

* 검색
    ![boolean_query-search-20190129](https://static.toastoven.net/prod_search/boolean_query-search-20190129.png)
    1. "boolean"을 선택합니다.
    2. &, |, (, ), ! 을 이용한 불리언 질의를 입력합니다.
* 연산자 우선순위
    * (), !, &, | 순입니다.
* 피연산자 처리
    * 피연산자는 Exact matching으로 처리됩니다.
    * q=나이키 신발&q_option=boolean
        * 검색이 되는 검색 대상
            * "인기 나이키 신발 할인"
            * "인기 나이키신발 할인"
        * 검색이 안되는 검색 대상
            * "인기 나이키 할인 신발"
                * "나이키"와 "신발" 사이에 다른 단어가 들어 있기 때문임
            * "인기 신발 나이키 할인"
                * "나이키"와 "신발"의 순서가 다르기 때문임

### 문서 가중치 지정
* 필드 설정
    ![documents_boosting-field-20190129](http://static.toastoven.net/prod_search/documents_boosting-field-20190129.png)
* 색인
    * 테스트를 위해 아래 데이터를 색인합니다.
    ```
    [
      {
        "action": "add",
        "id": "id-1",
        "weight": 0.1,
        "fields": {
          "title" : "나이키"
        }
      },
      {
        "action": "add",
        "id": "id-2",
        "weight": 0.9,
        "fields": {
          "title" : "나이키"
        }
      }
    ]
    ```
    * "id-1"에는 "weight"를 0.1, "id-2"에는 "weight"를 0.9로 지정합니다.
    * "weight"는 0.0 ~ 1.0 사이의 값을 입력할 수 있습니다.
    <br><br>
* 검색
    ![documents_boosting-search-20190129](http://static.toastoven.net/prod_search/documents_boosting-search-20190129.png)
    * "나이키"로 검색합니다.
    <br><br>
* 검색 결과
    ```
    "itemList": {
      "item": [
        {
          "_RELEVANCE": 0.43333334,
          "_RANK": 1,
          "_ID": "id-2",
          "title": "<b>나이키</b>"
        },
        {
          "_RELEVANCE": 0.20877191,
          "_RANK": 2,
          "_ID": "id-1",
          "title": "<b>나이키</b>"
        }
      ]
    }
    ```
    * "weight"를 높게 부여한 "id-2" 문서가 검색 결과 상위에 노출됩니다.
    <br><br>
* weight 반영 비율 조정
    * doc_weight_ratio 파라미터를 이용해서 반영 비율을 조정합니다.
        ```
        curl -G -XGET 'https://alpha-api-search.cloud.toast.com/search/v1.0/appkeys/bJsVUwrftmEl4K7D/serviceids/test/search?start=1&size=10&q_option=and,title*1.0&return=&passage.title=180&doc_weight_ratio=0.1' --data-urlencode q='나이키' --data-urlencode highlight='<b>,</b>'
        ```
        * 0.0 ~ 1.0 사이의 값을 입력할 수 있습니다.
        * default는 1.0입니다.
* 사용자가 입력한 질의와 문서의 유사도(similarity) 반영 비율 조정
    * similarity_ratio 파라미터를 이용해서 반영 비율을 조정합니다.
        ```
        curl -G -XGET 'https://alpha-api-search.cloud.toast.com/search/v1.0/appkeys/bJsVUwrftmEl4K7D/serviceids/test/search?start=1&size=10&q_option=and,title*1.0&return=&passage.title=180&similarity_ratio=0.1' --data-urlencode q='나이키' --data-urlencode highlight='<b>,</b>'
        ```
        * 0.0 ~ 1.0 사이의 값을 입력할 수 있습니다.
       * default는 1.0입니다.
* Tip
    * similarity_ratio와 doc_weight_ratio를 조절해서 검색 결과 출력 순서를 커스터마이징할 수 있습니다.

### 문서 랭킹 지정
* 필드 설정
    ![documents_ranking-field-20190129](http://static.toastoven.net/prod_search/documents_ranking-field-20190129.png)
* 색인
    * 테스트를 위해 아래 데이터를 색인합니다.
    ```
    [
      {
        "action": "add",
        "id": "id-1",
        "ranking": 2,
        "fields": {
          "title" : "나이키"
        }
      },
      {
        "action": "add",
        "id": "id-2",
        "ranking": 1,
        "fields": {
          "title" : "나이키"
        }
      }
    ]
    ```
    * "id-1"에는 "ranking"을 2, "id-2"에는 "ranking"을 1로 지정합니다.
    * "ranking"은 1 ~ 10000 사이의 값을 입력할 수 있습니다.
    <br><br>
* 검색
    ![documents_ranking-search-20190129](http://static.toastoven.net/prod_search/documents_ranking-search-20190129.png)
    * "나이키"로 검색합니다.
    <br><br>
* 검색 결과
    ```
    "itemList": {
      "item": [
        {
          "_RELEVANCE": 10000.151,
          "_RANK": 1,
          "_ID": "id-2",
          "title": "<b>나이키</b>"
        },
        {
          "_RELEVANCE": 9999.151,
          "_RANK": 2,
          "_ID": "id-1",
          "title": "<b>나이키</b>"
        }
      ]
    }
    ```
    * "ranking"을 1로 지정한 "id-2" 문서가 검색 결과 1등으로 노출됩니다.
    * "ranking"을 동일하게 지정한 경우 사용자가 입력한 질의와 유사도가 높은 문서가 먼저 노출됩니다.
    <br><br>

### 필드 설정 다운로드/업로드
* 설정 다운로드
    ![field-download-20190129](https://static.toastoven.net/prod_search/field-download-20190129.png)
    1. "설정 다운로드" 버튼을 클릭해서 현재 설정을 다운로드합니다.
		<br><br>
* 설정 업로드
    ![field-upload-20190129](https://static.toastoven.net/prod_search/field-upload-20190129.png)
    1. "설정 업로드" 버튼을 클릭해서 설정을 업로드합니다.
        * 설정된 필드가 하나도 없을 때만 "설정 업로드" 버튼이 노출됩니다.

## 상세 가이드

### 필드 타입
* 필드 타입 선택 화면
    ![detail-field_type-20190129](http://static.toastoven.net/prod_search/detail-field_type-20190129.png)
* text
    * "검색"할 필드일 경우 선택합니다.
    * 형태소 분석을 합니다.
        * 필드 값이 "나이키운동화"일 경우 "나이키운동화", "나이키 운동화", "나이키" 또는 "운동화"로 검색했을 때 검색 결과가 나옵니다.
    * 최대 사이즈는 32,768Byte입니다.
* keyword
    * "필터", "정렬", "요약"할 필드일 경우 선택합니다.
    * 형태소 분석을 하지 않습니다.
        * 필드 값이 "나이키운동화"일 경우 "나이키운동화"로만 "필터", "정렬", "요약"이 됩니다.
        * 필드 값이 "나이키 운동화"일 경우 "나이키 운동화"로만 "필터", "정렬", "요약"이 됩니다.
    * 최대 사이즈는 128Byte입니다.
* byte
    * 1byte 정수형입니다.
    * -128 ~ 127까지 표현 가능합니다.
* short
    * 2byte 정수형입니다.
    * -32,768 ~ 32,767까지 표현 가능합니다.
* integer
    * 4byte 정수형입니다.
    * -2^31 ~ 2^31 - 1까지 표현 가능합니다.
* long
    * 8byte 정수형입니다.
    * -2^63 ~ 2^63 - 1까지 표현 가능합니다.
* float
    * 4byte 실수형입니다.    
    * -3.4E38 ~ 3.4E38까지 표현 가능합니다.
* double
    * 8byte 실수형입니다.
    * -1.7E308 ~ 1.7E308까지 표현 가능합니다.
* boolean
    * 1byte
    * true or false
* date
    * 필드 값이 날짜인 경우 선택합니다.
    * 지원하는 날짜 형식
        * yyyy-MM-dd
            * 예제) 2017-09-22
        * yyyy-MM-dd’T’HH:mm:ss
            * 예제) 2017-09-22T15:39:28
        * yyyy-MM-dd’T’HH:mm:ss'Z'
            * 예제) 2017-09-22T15:39:28Z
        * yyyy-MM-dd'T'HH:mm:ss.SSS
            * 예제) 2017-09-22T15:39:28.248
        * yyyy-MM-dd'T'HH:mm:ss.SSS'Z'
            * 예제) 2017-09-22T15:39:28.248Z
* text를 제외한 모든 필드 타입은 배열 형태로 입력 가능합니다.
    * ["나이키", "아디다스"]
    * [1.0, 2.0]
    * ["2017-09-22T15:39:28", "2017-09-22T15:39:29"]

### 형태소 분석
* 형태소 분석기 선택 화면
    ![detail-analysis-20190129](http://static.toastoven.net/prod_search/detail-analysis-20190129.png)
* default
    * 형태소 분석기를 이용해 단어을 분리한다.
      * 예제) "나이키 신상슈즈" -> "나이키" "신상" "슈즈"
* whitespace
    * whitespace를 구분자로 토큰을 분리한다.
      * 예제) "나이키 신상슈즈" -> "나이키" "신상슈즈"
* bigram
    * 2글자씩 단어를 분리한다.
      * 예제) "나이키 신상슈즈" -> "나이" "이키" "신상" "상슈" "슈즈"

### ACL
* ACL 설정 화면
    ![detail-acl-20190129](http://static.toastoven.net/prod_search/detail-acl-20190129.png)
* 입력 형식
    * IP 형식으로 입력 가능합니다.
        * 예제) 202.179.177.21
    * CIDR 형식으로 입력 가능합니다.
        * 예제) 202.179.177.0/24
    * IP 또는 CIDR 을 여러 개 입력 가능합니다.
        * 예제) 202.179.177.21, 202.179.177.0/24
    * all 일 경우 모두 매칭 됩니다.
    * 값이 비어 있을 경우 모두 매칭 안됩니다.  
* 허용, 거부 둘 다에 매칭이 될 경우 거부됩니다.
* 허용, 거부 둘 다에 매칭이 안될 경우 거부됩니다.


## 클라이언트 예제 코드
* 파일 업로드 방식의 색인 예제 코드입니다.

### java
* dependency
``` java
compile group: 'org.apache.httpcomponents', name: 'httpclient', version: '4.5.6'
compile group: 'org.apache.httpcomponents', name: 'httpmime', version: '4.5.6'
```
* 색인(파일 업로드 방식)
``` java
package com.toast.cloud.cloudsearch.client;

import org.apache.http.HttpEntity;
import org.apache.http.client.ClientProtocolException;
import org.apache.http.client.ResponseHandler;
import org.apache.http.client.methods.HttpUriRequest;
import org.apache.http.client.methods.RequestBuilder;
import org.apache.http.entity.ContentType;
import org.apache.http.entity.mime.HttpMultipartMode;
import org.apache.http.entity.mime.MultipartEntityBuilder;
import org.apache.http.impl.client.CloseableHttpClient;
import org.apache.http.impl.client.HttpClients;
import org.apache.http.util.EntityUtils;

import java.io.File;
import java.io.IOException;
import java.io.PrintWriter;

public class IndexingClient {

  public static void main(String[] args) throws IOException {

    String documents = ""
      + "[\n"
      + "  {\n"
      + "    \"action\": \"add\",\n"
      + "    \"id\": \"id-1\",\n"
      + "    \"fields\": {\n"
      + "      \"title\": \"[무료배송]나이키 슈즈 195종!!\",\n"
      + "      \"body\": \"명불허전 나이키 인기슈즈 괜히 잘 팔리는게 아니죠~~ 나이키 핫!슈즈 195종★ 하나쯤은 있어야 하지 않아??\"\n"
      + "    }\n"
      + "  }\n"
      + "]";

    File tempFile = File.createTempFile("documents-",".json", new File("/tmp/"));
    tempFile.deleteOnExit();

    PrintWriter printWriter = new PrintWriter(tempFile);
    printWriter.println(documents);
    printWriter.close();

    try (CloseableHttpClient httpclient = HttpClients.createDefault()) {

      // build multipart upload request.
      HttpEntity data = MultipartEntityBuilder.create()
        .setMode(HttpMultipartMode.BROWSER_COMPATIBLE)
        .addBinaryBody("file", tempFile, ContentType.DEFAULT_BINARY, tempFile.getName())
        .build();

      // build http request and assign multipart upload data.
      HttpUriRequest request = RequestBuilder
    	  .post("https://alpha-api-search.cloud.toast.com/indexing/v1.0/appkeys/bJsVUwrftmEl4K7D/serviceids/test/indexing")
        .setEntity(data)
        .build();

      System.out.println("Executing request " + request.getRequestLine());

      // Create a custom response handler.
      ResponseHandler<String> responseHandler = response -> {
        int status = response.getStatusLine().getStatusCode();
        if (status >= 200 && status < 300) {
          HttpEntity entity = response.getEntity();
          return entity != null ? EntityUtils.toString(entity) : null;
        } else {
          throw new ClientProtocolException("Unexpected response status: " + status);
        }
      };
      String responseBody = httpclient.execute(request, responseHandler);
      System.out.println(responseBody);
    }
  }
}
```

### php
* 색인(파일 업로드 방식)
``` php
<?php
    $documents = ""
      . "[\n"
      . "  {\n"
      . "    \"action\": \"add\",\n"
      . "    \"id\": \"id-1\",\n"
      . "    \"fields\": {\n"
      . "      \"title\": \"[무료배송]나이키 슈즈 195종!!\",\n"
      . "      \"body\": \"명불허전 나이키 인기슈즈 괜히 잘 팔리는게 아니죠~~ 나이키 핫!슈즈 195종★ 하나쯤은 있어야 하지 않아??\"\n"
      . "    }\n"
      . "  }\n"
      . "]";

    $file = DIRECTORY_SEPARATOR.trim(sys_get_temp_dir(), DIRECTORY_SEPARATOR).DIRECTORY_SEPARATOR.ltrim("documents.json", DIRECTORY_SEPARATOR);
    file_put_contents($file, $documents);

    register_shutdown_function(function() use($file) {
        unlink($file);
    });

    $data = array(
        'file' => curl_file_create($file, "application/json", basename($file))
    );

    $ch = curl_init();
    curl_setopt($ch, CURLOPT_URL,"https://alpha-api-search.cloud.toast.com/indexing/v1.0/appkeys/bJsVUwrftmEl4K7D/serviceids/test/indexing");
    curl_setopt($ch, CURLOPT_POST, 1);
    curl_setopt($ch, CURLOPT_HTTPHEADER, array("Content-Type:multipart/form-data; charset=UTF-8"));
    curl_setopt($ch, CURLOPT_POSTFIELDS, $data);
    curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
    curl_setopt($ch, CURLOPT_HEADER, true);

    $response = curl_exec($ch) or die(curl_error($ch));
    print_r($response);

    curl_close($ch);
?>
```
