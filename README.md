# rd_control
<img width="447" height="228" alt="image" src="https://github.com/user-attachments/assets/828dfacf-a6dd-4096-bd93-d158c15390ac" />

BRAM에 존재하는 데이터를 불러오는 방식을 padding에 따라 3가지 경우로 나눈다.
case_1: 세로 패딩과 윗 패딩이 존재하는 경우
case_2: 세로 패딩만 존재하는 경우
case_3: 세로 패딩과 아래 패딩이 존재하는 경우
1개의 주소에 16비트로 packing된 데이터가 4개 존재하는 경우 case를 고려해서 주소를 읽어 오는 방법

<img width="438" height="395" alt="image" src="https://github.com/user-attachments/assets/61fe357b-8eb3-4478-a5bf-ff71ea46f15b" />

1. row_cnt 값을 증가시켜 필요로 하는 데이터가 저장된 주소 한 줄을 읽어온다.
2. row_cnt가 필요로 하는 데이터 한줄을 전부 읽어온다면 0으로 보내고 column_cnt를 증가시킨다.
3. 하나의 channel에 필요로 하는 데이터를 전부 읽은 경우 channel_cnt를 증가시켜 다음 채널로 넘어간다.
4. 이 모든 과정을 B_row_cnt와 B_column_cnt를 사용해 반복 진행하며 BRAM에 데이터 전체를 읽어온다. 
