# octohug

## the octopress to hugo migrator

To use octohug, compile octohug.go and drop octohug into your octopress blog directory. octohug does this:

* converts the octopress post header to a hugo post header
* converts octopress categories and tags to the hugo equivalent in the post header
* replaces include_file in the octopress post body with the file content

## gotchas
I had a couple of octopress posts where the title attribute was spread across two lines. There were only two posts like this so I didn't think it worth the hassle of coding a solution. It's much easier to just open the converted file and delete the errant line. You'll know you have one as hugo will throw an error with a two line title.

octohug ignores a lot of octopress headers as I don't use them. Fork and change to suit. There will prolly be lots more headers it doesn't know about that I don't use so if you get weird hugo errors, have a look in the converted file's header and fork/fix for your environment.

## what to do
let's say you have an octopress blog in ~/octo/blog and a shiny new, empty hugo blog in ~/hugo/blog.
<pre>
	go build 
	cp octohug ~/octo/blog
	cd ~/octo/blog
	./octohug
</pre>
you'll now have a ~/octo/blog/content/post directory
<pre>
	cp -r ~/octo/blog/content/post ~/hugo/blog/content
</pre>
if there are octopress header attributes octohug doesn't know about they'll end up in the hugo header. Fork/fix to suit.

## sorting the feed
the octopress feed is at atom.xml while the hugo one is at index.xml so I needed an entry in .htaccess:
<pre>
	RedirectMatch 301 ^/blog/atom.xml$ http://codebrane.com/blog/index.xml
</pre>

## give octopress a big hug
octopress got me out of wordpress. It's been superb and a great introduction to static blogs and sites. So long octopress and thanks for al the posts!
