Download Link: https://assignmentchef.com/product/solved-cs311-assignment-6
<br>
Add caches to the simulated memory system.

<ul>

 <li>Add one cache between the IF stage and the main memory. Let us call this the “level 1 instruction cache” or the L1i-cache.</li>

 <li>Add one cache between the MA stage and the main memory. Let us call this the “level 1 data cache” or the L1d-cache.</li>

</ul>

The configurations of the caches are as follows:

<table width="328">

 <tbody>

  <tr>

   <td width="91">Cache size</td>

   <td width="55">8B</td>

   <td width="61">32B</td>

   <td width="61">128B</td>

   <td width="61">1kB</td>

  </tr>

  <tr>

   <td width="91">Latency</td>

   <td width="55">1 cycle</td>

   <td width="61">2 cycles</td>

   <td width="61">4 cycles</td>

   <td width="61">8 cycles</td>

  </tr>

  <tr>

   <td width="91">Line Size</td>

   <td width="55"></td>

   <td colspan="2" width="121">4B</td>

   <td width="61"></td>

  </tr>

  <tr>

   <td width="91">Associativity</td>

   <td width="55"></td>

   <td colspan="2" width="121">2</td>

   <td width="61"></td>

  </tr>

  <tr>

   <td width="91">Write Policy</td>

   <td width="55"></td>

   <td colspan="2" width="121">Write Through</td>

   <td width="61"></td>

  </tr>

 </tbody>

</table>

Perform the following analyses:

<ol>

 <li>First fix the size of the L1d-cache at 1kB. Vary the size of the L1i-cache from 4B to 1kB (remember to change latency accordingly), and study the performance (instructions per cycle). Plot your results for the different benchmarks.</li>

 <li>Now fix the size of the L1i-cache at 1 kB. Vary the size of the L1d-cache from 4B to 1kB, and plot your results for the different benchmarks.</li>

 <li>In your report, correlate the nature of the benchmark to the observed plot.</li>

 <li>Create a toy-benchmark that shows significant performance improvementwhen the L1i-cache is increased from 32B to 128B. Assume favorable L1dcache size.</li>

 <li>Create a toy-benchmark that shows significant performance improvementwhen the L1d-cache is increased from 32B to 128B. Assume favorable</li>

</ol>

L1i-cache size.

Note: Implement a single “Cache” class in the processor/memorysystem package. The L1i-cache and the L1d-cache must be objects of this class.

1

<h2>Tips</h2>

<ul>

 <li>Implement a separate “CacheLine” class. It will have, among other fields, an integer array field named data, and an integer field named tag.</li>

 <li>In the Cache class, instantiate an array of CacheLine’s of size equal to the number of lines required.</li>

 <li>In the Cache class, have a function: cacheRead(int address). This function is called when the pipeline makes a read (load) request. This function takes an address as an argument. If the line corresponding to this address is present in the cache, it returns the corresponding 4B value to the pipeline. If the line corresponding to this address is not present, it calls the handleCacheMiss()</li>

 <li>In the Cache class, have a function: cacheWrite(int address, int value). This function is called when the pipeline makes a write (store) request. This function takes an address and a value as arguments. If the line corresponding to this address is present in the cache, the value is written to the line, the line written to the main memory, and (in parallel) the pipeline is informed that the store has completed. If the line corresponding to this address is not present, it calls the handleCacheMiss()</li>

 <li>In the Cache class, have a function: handleCacheMiss(int address). This function requests the main memory for the given line.</li>

 <li>In the Cache class, have a function: handleResponse(). This function handles the response from the lower level in the memory system (in our case, the main memory). The response is a cache line. This line has to be placed in the appropriate position in the cache. If there is a read request waiting for this line, the pipeline must be given the value. If there is a write request waiting, the value is written to the line, the line written to the main memory, and (in parallel) the pipeline is informed that the store has completed.</li>

 <li>Note: the function descriptions given above are merely to get you started.</li>

</ul>

You will have to modify the function prototypes as you see fit.

<ul>

 <li>Don’t forget: the hashes still have to match!</li>

</ul>