# count-island
# c
첫째 줄에는 지도의 너비 w와 높이 h가 주어진다. w와 h는 50보다 작거나 같은 양의 정수이다. 둘째 줄부터 h개 줄에는 지도가 주어진다. 1은 땅, 0은 바다이다. 위,아래,왼쪽,오른쪽,대각선으로 연결되면 하나의 섬이다. 섬의 개수를 출력하는 프로그램을 작성해보자! 

#include <stdio.h>
#include <stdlib.h>

int island[100][100];
int visit[50][50]={0};
int dx[8]={-1,1,0,0,-1,1,-1,1}; //위 아래 오른쪽 왼쪽 대각선까지 붙어있다면 1개의 섬으로 취급  
int dy[8]={0,0,-1,1,1,1,-1,-1};
int cnt=0,i,j,w=1,h=1;

void dfs(int y, int x){
	visit[y][x]=1; //방문했다 표시  
	for(i=0;i<8;i++){
		int a=y+dx[i];
		int b=x+dy[i];
		if(a<0 && a>=w && b<0 && b>=h){ //지도밖으로 벗어나면  
			continue;}
		if(island[a][b]==1 && visit[a][b]==0){ //방문하지 않고 섬이 있는곳  
			dfs(a,b);}} }


void init(){
	for(i=0;i<h;i++){
	    for(j =0;j<w;j++){ //반복을 위해서 섬과 방문을 초기화 시킨다  
		    island[i][j]=0; 
			visit[i][j]=0;}} }
			
			
void main(){
	printf("0 0 을 입력하면 프로그램이 종료됩니다!\n");
	while (1){
		init();
	    scanf("%d %d",&w,&h);
		if (w==0&&h ==0){
			break;}
	    for(i=0; i<h; i++){
		    for(j =0; j <w; j++){
		    	scanf("%d",&island[i][j]);}}
		cnt=0;
	    for(i=0; i<h; i++) {
		    for(j =0; j <w; j++){
		    	if(island[i][j]==1&&visit[i][j]==0){
		    		cnt++; //섬의 개수 증가  
		    		dfs(i,j);}}}	
	    printf("위의 지도에서 섬의 개수는: %d\n",cnt);} }
