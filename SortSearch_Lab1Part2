import java.util.Random;
import java.text.DecimalFormat;

/**
 *  SortSearch sets up an array of random numbers of size listsize to test several
 *  sorting and searching algorithms which will then be instrumented to compare the
 *  number of comparisons done and the execution times at various list sizes
 *  
 *  @author Mitchel Fry & Stephen Oliver
 *  @version CS260 Lab #1, 06/26/2016
 */
public class SortSearch
{
    private int listsize = 10;
    private final int RANGE = 100000;
    private int[ ] numList;
    private Random rand;
    //----Variables added for analysis----//
    private long count = 0;
    private double t1 = 0;
    private double t2 = 0;
    private long[] compares;
    private double[] times;

    /**
     * Default constructor, just initialize the numList array 
     */
    public SortSearch( )
    {
        numList = new int[ listsize];
        
        //Added for internal averaging of search metrics
        compares = new long[ 100];
        times = new double[ 100]; 
    }

    /**
     * Non-default constructor, initialize the numList array to the given size
     * 
     * @param size of array to create
     */
    public SortSearch( int size)
    {
        listsize = size;
        numList = new int[ listsize];
        
      //Added for internal averaging of search metrics
        compares = new long[ 100];
        times = new double[ 100]; 
    }

    /**
     * Fills the array with listsize integers
     */
    public void fillArray( )
    {
        rand = new Random( );

        for ( int i = 0; i < listsize; i++) {
            numList[ i] = rand.nextInt( RANGE);
        }
    }

    /**
     * Prints the entire array in indexed order
     */
    public void printArray( )
    {
        for ( int i = 0; i < numList.length; i++) {
            System.out.println( "Element " + i + ": " + numList[ i]);
        }
    }

    //================== Sorting Methods =======================      
    /**
     * Sorts the array using Insertion Sort logic
     */
    public void insertionSort( )
    {
    	count = 0;
    	t1 = getSystemTime();
    	
        for ( int i = 1; i < numList.length; i++) {
            // insert numList[i] into numList[0:i-1]
            int j, t = numList[ i];
            
            for ( j = i - 1; j >= 0 && t < numList[ j]; j--) {
                numList[ j + 1] = numList[ j]; //shuffle the empty space
                count ++;
            } 
            numList[ j + 1] = t; //assign t into the empty space
        }
        
        t2 = getSystemTime();
        printSortingMetrics("Insertion Sort", count, ((t2-t1)/1000000000.0));
    }
 
    /**
     * Sorts the array using Insertion Sort logic
     */
    public void selectionSort( )
    {
    	count = 0;
    	t1 = getSystemTime();
    	
        int t;
      
        for ( int i = 0; i < numList.length; i++) {
            t = i; //Index of the smallest element in this pass
            for ( int j = i+1; j < numList.length; j++) {
            	count++;
                if ( numList[ j] < numList[ t]) {
                    t = j;
                }
            }
            swap( i, t); //swap the values at these positions
        }
        
        t2 = getSystemTime();
        printSortingMetrics("Selection Sort", count, ((t2-t1)/1000000000.0));
    }

 
    /**
     * Sorts the array using Bubble Sort logic (bad way to sort)
     */
    public void bubbleSort( )
    {
    	count = 0;
    	t1 = getSystemTime();
    	
        for ( int out = numList.length - 1; out > 0; out--) { // outer loop (backward)
            for ( int in = 0; in < out; in++) { // inner loop (forward)
                if ( numList[ in] > numList[ in + 1]) { // out of order?
                    swap( in, in + 1);
                }
                count++;
            } 
        }
        
        t2 = getSystemTime();
        printSortingMetrics("Bubble Sort", count, ((t2-t1)/1000000000.0));
        
    }



    //================== Search Methods =======================    
    /**
     * A shell method for your linear search logic
     * 
     * @param searchNum the value to search for in the array 
     * @param runNum used for inserting items into analysis lists
     * @return returns true is searchNum is found in the array, otherwise false
     */
    public boolean containsLinear( int searchNum, int runNum)
    {
    	count = 0;
    	
    	t1 = getSystemTime();
    	for (int i = 0; i <= numList.length - 1; i++){
    		if (numList[i] == searchNum){
    			t2 = getSystemTime();
    			compares[runNum] = count++;
    			times[runNum] = (t2-t1);
    			return true;
    		}
    		count++;
    	}
    	compares[runNum] = count;
    	t2 = getSystemTime();
    	times[runNum] = (t2-t1);
        return false;
    }
  
    /**
     * A shell method for your binary search logic
     * 
     * @param searchNum the value to search for in the array 
     * @param runNum used for inserting items into analysis lists
     * @return returns true is searchNum is found in the array, otherwise false
     */
    public boolean containsBinary( int searchNum, int runNum)
    {
    	int m;
    	int h = numList.length - 1;
    	
    	count = 0;
    	
    	t1 = getSystemTime();
    	for (int l = 0; l <= h; l++, h--){
    		m = (l + h)/2;
    		if (numList[m] < searchNum){
    			l = m++;
    		}
    		else if (numList[m] > searchNum){
    			h = m--;
    		}
    		else {
    			t2 = getSystemTime();
    			compares[runNum] = count++;
    			times[runNum] = (t2-t1);
    			return true;
    		}
    		count++;
    	}
    	compares[runNum] = count;
    	t2 = getSystemTime();
    	times[runNum] = (t2-t1);
        return false;
    }
    
    /**
     * This method can be used to print your results of a run.  Re-factor this as appropriate for
     * what ever method you choose to collect your data points.  I would suggest writing to a 
     * comma delimited text file so that you can easily import the data into a spreadsheet for
     * graphing and analysis.
     * 
     * @param searchType A string stating the type of search that was done
     */
    private void printSearchMetrics(String searchType)
    {
    	int avg = 0;
    	System.out.println("****Emperical Measures For: " + searchType);
    	//Get average of compares for all 100 searches
    	for (int i = 0; i < compares.length; i++){
    		avg += compares[i];
    	}
    	avg /= 100;
    	System.out.println("****Average Compares: " + avg);
    	avg = 0;
    	//Get average runtime for all 100 searches
    	for (int i = 0; i < times.length; i++){
    		avg += times[i];
    	}
    	avg /= 100;
    	System.out.println("****Average Runtime: " + avg + " nS");
    	System.out.println(" ");
    }
    
    /**
     * This method can be used to print your results of a run.  Re-factor this as appropriate for
     * what ever method you choose to collect your data points.  I would suggest writing to a 
     * comma delimited text file so that you can easily import the data into a spreadsheet for
     * graphing and analysis.
     * 
     * @param sortType A string stating the type of sort that was done
     */
    public void printSortingMetrics( String sortType, long compares, double time)
    {
        //This is where you would put the time, compares, and move counters
    	DecimalFormat df3 = new DecimalFormat(".###");
    	
        System.out.println("****Emperical Measures For: " + sortType);
        System.out.println("****Element Comparisons Made: " + compares);
        System.out.println("****Clock Time Measurement: " + df3.format(time) +" S");
        System.out.println(" ");
    }
    
    //============ Private utility methods ==============
    /**
     * This value is the internal system time that is the measured in
     * the number of nano-seconds since Jan. 1, 1970.
     * 
     * @return The current time of the system clock
     */
    private double getSystemTime( )
    {
        return System.nanoTime( );
    }

    
    /**
     * Swap routine to re-order the ith and jth array values
     *
     * @param  i   an array location to be swapped with j
     * @param  j   an array location to be swapped with i
     */
    private void swap(int i, int j)
    {
        int temp = numList[i];
        numList[i] = numList[j];
        numList[j] = temp;
    }

    
    //============Program entry point MAIN======================
    /**
     * Standard class method "main".  Modify this to collect the
     * empirical metrics data on the sorting and searching methods
     */
    public static void main( String[ ] args)
    {
        int i = 1;
        Random rand = new Random( ); 
        
        //Sort Tests------------------------------------------//
        for ( i = 1; i <= 10; i++) {
            SortSearch test = new SortSearch( 10000 * i);
            System.out.println("------This is run number: " + i+ "------");
            
            test.fillArray();
            test.insertionSort();
            //test.printArray();
            
            test.fillArray();
            test.selectionSort();
            //test.printArray();
            
            test.fillArray();
            test.bubbleSort();
            //test.printArray();
            
            //Search Tests----------------------------------------//
            for (int x = 1; x<= 100; x++){
            	int num = rand.nextInt(100000);
            	test.containsBinary(num, (x-1));
            }
            test.printSearchMetrics("Binary Search"); //Print the average of the metrics
            
            for (int x = 1; x<= 100; x++){
            	int num = rand.nextInt(100000);
            	test.containsLinear(num, (x-1));
            }
            test.printSearchMetrics("Linear Search"); //Print the average of the metrics
            
            }
    }	
}
