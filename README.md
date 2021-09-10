# 발생오류 목록
## 1. sql 확인 시 커넥션 에러 발생
> **해결사항** : 디비버로 MySql커넥션을 새로 잡음

## 2. 서버실행시 Bean 생성 오류
> **원인** : mapper 파일인 WriteDao.xml에서의 오타 발생. 때문에 DTO의 위치를 찾지 못하고 서버가 다운됨. <br>
> **해결사항** : 정확한 위치를 기재해 오류 해결
```html
수정 전 : <select id="selectByUid" resultType="com.lec.spring.WriteDTO"> 
수정 후 : <select id="selectByUid" resultType="com.lec.spring.domain.WriteDTO">
```

## 3. 수정완료 후 view 페이지 uid오류
> **원인** : updateOk.jsp 파일에서의 오타. uid가 넘어가지 않음.<br>
> **해결사항** : updateOk.jsp파일에서 uid를 넘기는 부분의 코드 수정
```java
수정 전 : location.href = "view.do?uid=${uid}";
수정 후 : location.href = "view.do?uid=${param.uid}";
```

## 4. 삭제시 Sql문 오류
>**원인** : mapper파일인 WriteDAO.xml 파일에서의 오타 발생.
>**해결사항** : 해당 파일의 Sql문 코드 수정
```sql
수정 전 : DELETE FROM test_write WHERE uid = #{uid} 
수정 후 : DELETE FROM test_write WHERE wr_uid = #{uid}
```