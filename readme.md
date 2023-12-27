# Benchmark of file and image generation

## Benchmark protocol

This is a benchmark designed to test how fast WeeWX generates the files and
images of the Seasons skin, using one year of data.

1. Download and unpack the benchmark:
 
    ```shell
    cd /var/tmp
    wget -O weewx-benchmark-master.tar.gz https://github.com/weewx/weewx-benchmark/archive/master.tar.gz
    tar xvf weewx-benchmark-master.tar.gz
    ```

2. This benchmark will work _as is_ for Version 5.0.0b13 or later. However, for earlier
   versions you must make two modifications in the configuration file `weewx.conf`:

    - Set `WEEWX_ROOT` to the location of the benchmark:
   
          WEEWX_ROOT=/var/tmp/weewx-benchmark-master
   
    - Set `SQLITE_ROOT` to the location of the archive directory:

          SQLITE_ROOT=/var/tmp/weewx-benchmark-master/archive
 
3. Because this test is of how long it takes to create and populate the subdirectory
   `weewx-benchmark-master/public_html`, it must be empty before you start.

   ```shell
   rm -r weewx-benchmark-master/public_html
   ```

4. If you are on a laptop, plug it in!

5. Run the benchmark. For Version 5, use `weectl report`. For Version 4, use `wee_reports`

   ```shell
   weectl report run --config weewx-benchmark-master/weewx.conf
   ```
   
6. The benchmark will print the generation time for the files and images
   to standard output. Make sure there are 21 files and 68 images. If not, there
   may have been something in `weewx-benchmark-master/public_html`. Go back and do
   step 3 again.

7. Add your results to the wiki page [_Benchmarks of file and image
   generation_](https://github.com/weewx/weewx/wiki/Benchmarks-of-file-and-image-generation)
