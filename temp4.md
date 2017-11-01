# Algorithm

- Bubble Sort
- Selection Sort
- Quick Sort
- Merge Sort

## Bubble Sort

```java
public int[] sort(int[] data) {	
	for(int i=data.length-1; i>0; i--) {
		for(int j=0; j<i; j++) {
			if(data[j] > data[j+1]) {
				int temp = data[j+1];
				data[j+1] = data[j];
				data[j] = temp;
			}
		}
	}
	return data;
}
```

## Selection

```java
public void sort(int[] data) {
		
	int size = data.length;
	int min = 0;
	
	for(int i=0; i<size; i++) {
		// 첫번째 값을 최소값으로 가정
		min = i;
		for(int j=i+1; j<size; j++) {
			// 최소값보다 작은 값이면 min 변경
			if(data[min] > data[j]) {
				min = j;
			}
			int temp = data[min];
			data[i] = data[min];
			data[min] = temp;
		}
	}
}
```

## Quick Sort

```java
public int[] sort(int[] data, int left, int right) {
		
	int originalL = left;
	int originalR = right;
	int pivot = (left+right)/2;
	
	// 한 번 while문을 돌면 pivot를 중심으로 좌 우가 나뉜다
	while(left <= right) {
		// 왼쪽에서는 pivot보다 큰 값을 찾고
		while(data[left] < data[pivot]) left++;
		// 오른쪽에서는 pivot보다 작은 값을 찾는다
		while(data[right] > data[pivot]) right--;
		
		// left > right 인 경우는 이미 정렬이 되어 있는 케이스
		if(left <= right) {
			int temp = data[right];
			data[right] = data[left];
			data[left] = temp;
			left++;
			right--;
		}
	}
	
	// 위에서 나뉜 값을 좌 우로 재귀호출해준다
	if(originalL < right) {
		sort(data, originalL, right);
	}
	if(left < originalR) {
		sort(data, left, originalR);
	}
	
	return data;
}
```

## Merge Sort

#### sorting

```java
public int[] sort(int[] data) {
		
	int length = data.length;
	
	if(length == 1) return null;
	
	int[] leftArray = new int[length/2];
	int[] rightArray = new int[length-length/2];
	
	System.arraycopy(data, 0, leftArray, 0, length/2);
	System.arraycopy(data, length/2, rightArray, 0, length-length/2);
	
	sort(leftArray);
	sort(rightArray);
	
	merge(leftArray, rightArray, data);
	
	return data;
}
```

#### Merging

```java
public void merge(int[] left, int[] right, int[] whole) {
		
	int left_length = left.length;
	int right_length = right.length;
	
	int left_position = 0;
	int right_position = 0;
	int whole_position = 0;
	
	// 왼쪽 배열을 먼저 기준으로 잡는다
	while(left_position < left_length) {
		// 왼쪽 배열 기준 오른쪽 상태
		if(right_position < right_length) {
			if(left[left_position] < right[right_position]) {
				whole[whole_position] = left[left_position];
				left_position++;
				// 참고 - 같을 경우는 뭐가 들어가도 상관 없음
			} else {
				whole[whole_position] = right[right_position];
				right_position++;
			}
			whole_position++;
		// 왼쪽 배열이 남은 상태에서 오른쪽 배열 소진
		} else {
			whole[whole_position] = left[left_position];
			whole_position++;
			left_position++;
		}
	}
	
	// 왼쪽 배열이 소진됬는데 오른쪽 배열이 아직 남아있는 경우
	while(right_position < right_length) {
		whole[whole_position] = right[right_position];
		whole_position++;
		right_position++;
	}
}
```

