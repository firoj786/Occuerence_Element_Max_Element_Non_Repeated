# Occuerence_Element_Max_Element_Non_Repeated

package com.nt.important.java8;

import java.util.Arrays;

import java.util.Collections;

import java.util.Comparator;

import java.util.HashMap;

import java.util.HashSet;

import java.util.List;

import java.util.Map;

import java.util.Optional;

import java.util.Set;

import java.util.function.Function;

import java.util.stream.Collectors;

/**
 * @author Firoj
 * 
 * @since 2022-01-05
 * 
 */

public class OccurenceElement {

	public static void main(String[] args) {
  
		List<Integer> list = Arrays.asList(1, 1, 2, 5, 1, 3, 2, 1, 2, 4, 3);
    
		//Using Collection find occurrence
		  Set<Integer> dist = new HashSet<Integer>(list);
      
		   for (Integer i : dist) {
       
		 System.out.println(i + ":" + Collections.frequency(list, i)); 
		  }
		 
		//Using stream api
		Map<Integer,Long> map = new HashMap<Integer,Long>(); 
    
		  map = list.stream().collect(Collectors.groupingBy(Function.identity(),Collectors.counting())); 
      
		 for(Map.Entry<Integer, Long> entrySet : map.entrySet()) {
     
		 System.out.println(entrySet.getKey()+"->"+entrySet.getValue());
     
		}
		 
		//Max element find using stream
		Optional<Integer> max = list.stream().max(Comparator.comparing(Integer:: valueOf));
    
		 if(!max.isEmpty()) 
     
			 System.out.println(max.get());
		 
		//Non repeating element using stream api
		List<Integer> filter = list.stream().filter(e -> Collections.frequency(list, e)==1).collect(Collectors.toList());
    
		for (Integer integer : filter) {
    
			System.out.println(integer);
		
		}
	}
}


1:4
2:3
3:2
4:1
5:1

1->4
2->3
3->2
4->1
5->1

5

5
4

