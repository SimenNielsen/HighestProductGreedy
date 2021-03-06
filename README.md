# HighestProductGreedy
Returns highest product of three numbers given an array of numbers.


highestThreeProductFromArray(numArray: number[]): number{
    if (numArray.length < 3) return null; // return if the array length is less than 3

    //We can acheive O(n) through keeping track of these 5 values

    let highest = Math.max(numArray[0], numArray[1]); // highest number of the 2 first numbers, to avoid full list loop we will change this as we loop through the array
    let lowest  = Math.min(numArray[0], numArray[1]); // lowest number of array, to avoid full list loop we will change this as we loop through the array
    let highestProductOf2 = numArray[0] * numArray[1]; // product of the 2 first numbers, this will update as we loop through the array
    let lowestProductOf2  = numArray[0] * numArray[1]; // lowest product of the 2 first numbers, this will update as we loop through the array
    let highestProductOf3 = numArray[0] * numArray[1] * numArray[2]; // product of the 3 first numbers, this will update as we loop through the array
    //loop through every number of element
    for(let i = 1; i < numArray.length; i++){
      /*  
      replace highestProductOf3 if current number 
      along with the largest product of 2 numbers is greater. 
      Since we have negative numbers we also need to check the lowestProductOf2
      */
      highestProductOf3 = Math.max(highestProductOf3, numArray[i]*highestProductOf2, numArray[i]*lowestProductOf2);
      /*  
      replace highestProductOf2 if current number 
      along with the largest number is greater. 
      Since we have negative numbers we also need to check the lowest number
      */
      highestProductOf2 = Math.max(highestProductOf2, numArray[i]*highest, numArray[i]*lowest);
      /*  
      replace lowestProductOf2 if current number 
      along with the largest number is smaller. 
      Since we have negative numbers we also need to check the highest number
      */
      lowestProductOf2 = Math.min(lowestProductOf2, numArray[i]*highest, numArray[i]*lowest);
    
      highest = Math.max(highest, numArray[i]);// replace highest number if current number is higher
      lowest = Math.min(lowest, numArray[i]); // replace lowest number if current number is lower
    }
    return highestProductOf3;
  }
