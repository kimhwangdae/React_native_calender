# React_native_calender
리엑트 네이티브 달력 ui

## 원하는 날짜는 초록색으로 아닌 날짜는 빨간색으로 만들기

reduce를 사용해서 위의 기능을 구현하였다.


![asdfasfasdf](https://user-images.githubusercontent.com/59689327/116563480-05c89f80-a93f-11eb-9d79-deba74d8795b.PNG)


```  const [markedDates,setmarkedDates]=useState(null)
  const [CalenderDay,SetCalendderDay]=useState([
    {date:'2021-05-22', confirm:false},
    {date:'2021-05-23', confirm:true},
    {date:'2021-05-24', confirm:false},
    {date:'2021-05-10', confirm:true},
    {date:'2021-05-04', confirm:false},
  ])
  ```

위와 같은 형태의 .json 형식의 data를 back에서 받으면
  
``` function DateSet(){
    let obj=CalenderDay.reduce((c,v)=>v.confirm?
        Object.assign(c,{[v.date]:{disabled:true,startingDay:true,color:'green',endingDay:true},})
        :Object.assign(c,{[v.date]:{disabled:true,startingDay:true,color:'red',endingDay:true},}) 
      ,{})
      console.log(obj)
    setmarkedDates(obj)
  }
  ```
  js에서 제공하는 배열 API인 reduce를 이용하여 새로운 객체를 만들어줬다.
  위 코드에서 c는 이전 객체를 가르키고 v는 현재 객체를 가르킨다.
  이것을 이용해서 CalenderDay state를 순회하며 Object.assign으로 새로운 객체를 만들어주어 setsate로 새로운 객체를 만들어주었다.
