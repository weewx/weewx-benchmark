# Benchmark of file and image generation

## Benchmark protocol

This is a benchmark designed to test how fast WeeWX generates the files and
images of the Seasons skin, using one year of data. Add your results to the
table at the end.

1. Make sure you have installed WeeWX V5.0.0b13 or later. _Earlier versions will
   not work!_
 
2. Download and unpack the test station data
 
    ```shell
    cd /var/tmp
    wget https://weewx.com/benchmarks/weewx-benchmark.tar.gz
    tar xvf weewx-benchmark.tar.gz
    ```

3. The test is of how long it takes to create and populate the subdirectory
   `weewx-benchmark/public_html`, so make sure it is _not_ present before
   continuing.

   ```shell
   rm -r weewx-benchmark/public_html
   ```

4. Run the benchmark, using `weectl report`

   ```shell
   weectl report run --config=weewx-benchmark/weewx.conf
   ```
   
5. The benchmark will print the generation time for the files and images
   to standard output. Make sure there are 21 files and 68 images. If not, there
   may have been something in `weewx-benchmark/public_html`. Go back and do
   step 3 again.

6. Add your results to the wiki page [_Benchmarks of file and image
   generation_](https://github.com/weewx/weewx/wiki/Benchmarks-of-file-and-image-generation)
