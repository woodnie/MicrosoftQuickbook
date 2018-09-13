### cURL - Invoke-WebRequest {#curl-invoke-webrequest}

    [cURL](http://curl.haxx.se/) (clients for URL) 是一款常用的命令行工具，它被用于基于URL传输数据，它支持HTTP， HTTPS，FTP等协议。其实，在Windows平台上，从Powershell 3.0开始也增加了一个类似的命令 [Invoke-WebRequest](http://technet.microsoft.com/en-US/library/hh849901(v=wps.630).aspx), 执行 Get-Help Invoke-WebRequest 会看到下面的帮助信息。注意看一下其中的ALIASES部分，curl赫然在列。也就是说，你可以直接使用curl作为命令名字，呵呵！

       Invoke-WebRequest的语法与cURL有所不同，但如果会用cURL，转换到使用Invoke-WebRequest非常简单，下面举几个使用cURL和Invoke-WebRequest操作ElasticSearch的例子 (cURL表示cURL.exe命令，Invoke-WebRequest则是Powershell中的的实现)：

*   cURL -XGET &amp;apos;localhost:9200/library/book/_search&amp;apos;
*   Invoke-WebRequest [http://localhost:9200/library/book/_search](http://localhost:9200/library/book/_search) **-Method** GET (GET操也作可以省略)
*   cURL -XPOST &amp;apos;localhost:9200/library&amp;apos;
*   Invoke-WebRequest [http://localhost:9200/library](http://localhost:9200/library) **-Method** POST
*   cURL -XPUT &amp;apos;localhost:9200/library/book/_mapping&amp;apos; -d @mapping.json
*   Invoke-WebRequest [http://localhost:9200/library/book/_mapping](http://localhost:9200/library/book/_mapping) -Method PUT **-InFile** mapping.json
*   cURL -XPOST &amp;apos;localhost:9200/blog/article&amp;apos; -d &amp;apos;{&quot;title&quot;:&quot;ElasticSearch&quot;}&amp;apos;
*   Invoke-WebRequest[http://localhost:9200/blog/article](http://localhost:9200/blog/article) -Method POST **-Body** &amp;apos;{&quot;title&quot;:&quot;ElasticSearch&quot;}&amp;apos;
*   cURL -XGET &amp;apos;localhost:9200/library/book/_search?q=title:crime&amp;pretty=true&amp;apos;
*   Invoke-WebRequest[http://localhost:9200/library/book/_search?q=title:ElasticSearch&quot;&amp;&quot;pretty=true](http://localhost:9200/library/book/_search?q=title:ElasticSearch'&'pretty=true-OutFile) **-OutFile** response.txt
*   cURL -XPOST &amp;apos;localhost:9200/library/book/_search?pretty=true&amp;apos; -d &amp;apos;{&quot;query&quot;:{&quot;term&quot;:{&quot;title&quot;:&quot;wp8.1&quot;}}}&amp;apos;
*   Invoke-WebRequest[http://localhost:9200/library/book/_search?pretty=true](http://localhost:9200/library/book/_search?q=title:ElasticSearch'&'pretty=true-OutFile) -Method POST **-Body**&amp;apos;{&quot;query&quot;:{&quot;term&quot;:{&quot;title&quot;:&quot;wp8.1&quot;}}}&amp;apos;
*   cURL -XPOST &amp;apos;localhost:9200/library/book/_search?pretty=true&amp;apos; -d&amp;apos;{&quot;query&quot;:{&quot;terms&quot;:{&quot;tags&quot;:[&quot;surface&quot;, &quot;wp8.1&quot;],&quot;minimum_match&quot;:2}}}&amp;apos;
*   Invoke-WebRequest[http://localhost:9200/library/book/_search?pretty=true](http://localhost:9200/library/book/_search?pretty=true) -Method POST -Body &amp;apos;{&quot;query&quot;:{&quot;terms&quot;:{&quot;tags&quot;:[&quot;surface&quot;, &quot;wp8.1&quot;],&quot;minimum_match&quot;:2}}}&amp;apos;
*   curl -XPUT localhost:9200/_cluster/settings -d &amp;apos;{&quot;transient&quot;:{&quot;cluster.routing.allocation.enable&quot;: none}}&amp;apos;
*   Invoke-RestMethod[http://localhost:9200](http://localhost:9200/library/book/_search?pretty=true)/_cluster/settings -Method PUT -Body &amp;apos;{&quot;transient&quot;:{&quot;cluster.routing.allocation.enable&quot;: &quot;none&quot;}}&amp;apos;
*   Invoke-RestMethod [http://localhost:9200/_cluster/settings](http://localhost:9200/_cluster/settings) -Method PUT -Body &amp;apos;{&quot;transient&quot;:{&quot;cluster.routing.allocation.cluster_concurrent_rebalance&quot;: &quot;6&quot;}}&amp;apos;

       除了Invoke-WebRequest，Powershell 3.0起还提供了[Invoke-RestMethod](http://technet.microsoft.com/en-us/library/hh849971.aspx) 命令，它专门用于向RESTful web服务发送HTTP和HTTPS数据。两个命令很相似，但也有不同，具体的不同可以参见《[Widnows PowerShell](http://books.google.com/books?id=Zx6-J2wQB0oC&pg=PA167&lpg=PA167&dq=invoke-restmethod+and+invoke-webrequest&source=bl&ots=Zr38M468bK&sig=1KVEnGoQGp4u6352f_iI5Hru3ns&hl=en&sa=X&ei=kS0VU_qEGdTmoATQp4KYAQ&ved=0CGMQ6AEwCQ)》一书。