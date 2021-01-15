# torch.nn.Conv2d

`목표` 
+ pytorch class 정리 
+ tensor error 발생시 수정. 
+ 이후 논문 구현에서 활용


## 1. class 구조 
+ ```class Conv2d(_ConvNd)```
    + Convolution layer 계열 class는 _ConvNd를 상속. 
+ ```__init___```
    + parameter
        + in_channels: int 
        + out_channels: int 
        + kernel_size: Union[T, Tuple[T, T]]  -> filter size(단일 정수)
        + stride: Union[T, Tuple[T, T]] = 1 -> 보폭, filter가 이동 정도(단일 정수) 
        + padding: Union[T, Tuple[T, T]] = 0  -> 이미지의 빈 영역추가(단일 정수), 이미지 크기 일치시키기 위해 사용
        + dilation: Union[T, Tuple[T, T]] = 1  -> filter의 point(pixel) 간의 갼격조절 (ex: Atrous)
        + groups: int = 1 
            + int = 1 -> 입력 전체에 대해 convolution 진행
            + int = n -> 입력을 n 개의 group으로 분리, 출력을 n개의 group으로 분리. 각각 mapping 후 convolution
        + bias: bool = True
        + padding_mode: str = 'zeros'
        
        
## 2. convolution 연산        
+ `Input Tensor` : (N, C, H, W)
     + N : Batch
     + C : Channel 
     + H : Height
     + W : Width 
+ `Output Tensor` : (N, C, H, W)    
     + N : Batch
     + C : Channel 
     + H : Height
     + W : Width 
+ `Convolution 연산`
     + N : Batch
     + C : Out_Channel
     + H : ![image](https://user-images.githubusercontent.com/61634628/104682792-dfd51180-5738-11eb-8705-71e8f44b7b8c.png)
     + W : ![image](https://user-images.githubusercontent.com/61634628/104682809-e9f71000-5738-11eb-9658-bac570c3e9a4.png)



