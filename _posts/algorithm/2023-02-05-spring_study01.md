---
layout: single
title : "[자료구조] ArrayList & LinkedList 구현 "
categories: [datastructure]
tag: [java, datastructure]
toc : true
author_profile: false
search: true
sidebar:
    nav: "counts"
---

### ArrayList / LinkedList 구현

#### 1. ArrayList vs LinkedList

ArrayList는 조회는 빠르지만 수정/삭제가 느리다

LinkedList는 조회는 느리지만 수정/삭제가 빠르다


<bold>ArrayList와 LinkedList 차이</bold>

![img2](../../../images/posts/datastructure/chapter01/1.png)

조회시 ArrayList는 4015인덱스(4번째 건물, 15층)이라는것을 알기 때문에 바로 들어가서 오른쪽으로 가서 엘리베이터 타면서 찾기가능
LinkedList는 인덱스가 없기 때문에 하나씩 다 찾아야 해서 조회하는데 시간이 오래걸린다

#### 2. ArrayList 구현

```java
package arraylist;

import java.util.List;

public class ArrayList {
	private Object[] elementData = new Object[100];
	private int size = 0;
	
	
	public boolean addLast(Object element) {
		elementData[size++] = element;
		return true;
	}
	
	public boolean add(int index, Object element) {
		for(int i = size-1; i >= index; i--) {
			elementData[i + 1] = elementData[i];
		}
		elementData[index] = element;
		size++;
		return true;
	}
	
	public Object[] getList(){
		return elementData;
	}
	
	public String toString(){
		String str = "[";
		
		for(int i = 0; i < size; i++) {
			str += elementData[i];
			if(i < size-1) {
				str += ",";
			}
		}
		str += "]";
		return str;
	}	
}
```


출처 
 1. [[생활코딩]자료구조-LIST](https://opentutorials.org/module/1335/8709)
