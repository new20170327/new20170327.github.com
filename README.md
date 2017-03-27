<h1 class="post-title">{{.Title}}</h1>
    <section class="post-content">
      {{.Content}}
    <footer class="post-footer">
      <section class="author">
        <h4>{{.Author}}</h4>
      </section>
<script type="text/javascript" src="./js/category.auto.js"></script>
<script type="text/javascript">
    window.onload = function() {
        var page = getQueryString("page")
        var count = pageCount()
        if (page == null) {
            page = 1
        }else {
            page = parseInt(page)
        }

        if(page > 1) {
            document.getElementById("nav").innerHTML += "<a class='newer-posts' href='?page="+(page - 1)+"'>← Newer Posts</a>"
        }

        document.getElementById("nav").innerHTML += "<span class='page-number'>Page "+page+" of "+count+"</span>"

        if(page < count) {
            document.getElementById("nav").innerHTML += "<a class='older-posts' href='?page="+(page + 1)+"'>← Older Posts</a>"
        }

        if (page <= count) {
            var result = get(page)
            for (var i=0;i<result.length;i++) {
                document.getElementById("content").innerHTML += "<article class='post'><header class='post-header'><span class='post-meta'><time datetime='"+result[i].date+"' itemprop='datePublished'>"+result[i].date+"</time><h2 class='post-title'><a href='./html/"+result[i].title+".html'>"+result[i].title+"</a></h2></header><section class='post-excerpt'><p>"+result[i].desc+"</p> <p><a href='./html/"+result[i].title+".html' class='excerpt-link'>Read More...</a></p></section></article>"
            }
        }
    }

</script>
