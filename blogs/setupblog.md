Setup Blog
===============================================================================

This is a blog post outlining the process of setting up a blog and hosting on
my own website.


Markdown
===============================================================================

It starts, naturally, with a markdown document:

```markdown
Setup Blog
===============================================================================

This is a blog post outlining the process of setting up a blog and hosting on
my own website.


Markdown
-------------------------------------------------------------------------------

It starts, naturally, with a markdown document:

You are looking at a Markdown document.
```

Before any posting to the site takes place, it is imperative that this document
is at, or near, final draft.

There is quite a lot of manual editing to be done at the end, and it makes
little sense to be doing this repeatedly as modifications are made.

Once the Markdown draft is completed, it is time to move on...

Unix Markdown command
-------------------------------------------------------------------------------

Markdown is--by design--a trivial markup language.

HTML is expressive but outlandishly complicated.

The markup language used for this website is HTML, so the Markdown draft will
need be converted into html somehow.

Fortunately, Unix already provides a utility that accomplishes 80% of what I
need.

The [markdown](https://linux.die.net/man/1/markdown) utility is a command-line
tool that parses markdown and spits to standard-out an approximate html text


The above markdown example converts as following
```
trevord.black$ markdown example.md 
<h1>Setup Blog</h1>

<p>This is a blog post outlining the process of setting up a blog and hosting on
my own website.</p>

<h2>Markdown</h2>

<p>It starts, naturally, with a markdown document:</p>

<p>You are looking at a Markdown document.</p>
```

To produce a file, simply pipe the output to a file:
```
trevord.black$ markdown example.md > example.html
```

Skeleton HTML
===============================================================================

The above html example is too simply to be correctly interpreted by a browser.

We want fancy stuff like font sizings and colors and emphasis. We also want
support for math rendering and code rendering. So we need to fill all of that
out.

All blogs on this website will follow a set pattern. I have a decent idea of
what I want that pattern to look like, so I just created a skeleton html file
that contained the superset of any functionality I perceive that I'll ever want
to add.

It's a fool's errand to try and build out every functionality I could ever
conceivably want, but, I find the following adequate for the time being

```html
<!DOCTYPE html>
<html>

<head>
    <title>

        <! TODO Put Title of blog here >

    </title>
    <meta charset='UTF-8'>
    <meta content='width=device-width, initial-scale=1' name='viewport'/>
    
    <meta name='description' content='Trevor David Black is a visual person.'>
    <meta name='keywords' content='computer science, computer graphics, graphics, rendering, programming, movies, video games, mathematics, linear algebra, photography, cinematography'>
    <meta name='author' content='Trevor David Black'>

    <link rel='stylesheet' type='text/css' href='/css/blogs.css'/>
    <link rel='shortcut icon' href='/favicon.png?v=e' />

    <! MathJax setup >
    <script>
        MathJax = {
            tex: {
                inlineMath: [['$', '$'], ['\\(', '\\)']]
            },
            chtml: {
                scale: 1.4
            }
        }    
    </script>
    <script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
    <script id="MathJax-script" async
          src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-mml-chtml.js">
    </script>

    <! PrismJS (Code highlighting) setup >
    <link href="/css/prism.css" rel="stylesheet" type="text/css" />
    <script src="/script/prism.js" type="text/javascript"></script>

</head>

<body>

    <div class='nav'>
        <div id='topnav'>
            <ul>
                <li>
                    <a href='/'>Home</a>
                </li>
                <li>
                    <a href='/blog'>Blog</a>
                </li>
                <li>
                    <a href='/photography'>Photography</a>
                </li>
                <li>
                    <a href='http://www.github.com/trevordblack' target='_blank'>Code</a>
                </li>
            </ul>
        </div>
    </div>
    
    <div id='header'>
        
        <! TODO Put Header of the article here >

    </div>

    <div id='article'>

        <div id='title'>
            <h1>
                <! TODO Put Title of the article here >
            </h1>
        </div>

        <div id='subtitle'>
            <h1>
                <! TODO Put Subtitle of the article here >
            </h1>
        </div>

        <! TODO Put Markdown output here >

    </div>

    <div id='footer'>
        
        <! TODO Put footer of the article here >

    </div>

    <div class='nav'>
        <div id='bottomnav'>
            <ul>
                <li>
                    <a href='/'>Home</a>
                </li>
                <li>
                    <a href='/blog'>Blog</a>
                </li>
                <li>
                    <a href='/photography'>Photography</a>
                </li>
                <li>
                    <a href='http://www.github.com/trevordblack' target='_blank'>Code</a>
                </li>
            </ul>
        </div>
    </div>

</body>

</html>
```

Sorry for the wall of text.

Looking through, you an see some basic functionality.
- Title
- Navigation bar at the top
- Navigation bar at the bottom
- Support for headers
- Support for footers
- Title of the article (same as Title)
- Subtitle of the article
- Article


Modifications to the Skeleton HTML
-------------------------------------------------------------------------------

The output of the markdown command line needs go in the article section:


```html
...

    <div id='article'>

        <div id='title'>
            <h1>
                <! TODO Put Title of the article here >
            </h1>
        </div>

        <div id='subtitle'>
            <h1>
                <! TODO Put Subtitle of the article here >
            </h1>
        </div>

        <! TODO Put Markdown output here >

    </div>

...
```

Becomes:

```html
...

    <div id='article'>

        <div id='title'>
            <h1>
                <! TODO Put Title of the article here >
            </h1>
        </div>

        <div id='subtitle'>
            <h1>
                <! TODO Put Subtitle of the article here >
            </h1>
        </div>

        <h1>Setup Blog</h1>

        <p>This is a blog post outlining the process of setting up a blog and hosting on
        my own website.</p>

        <h2>Markdown</h2>

        <p>It starts, naturally, with a markdown document:</p>

        <p>You are looking at a Markdown document.</p>

    </div>

...
```

But, we've included the title and subtitle in the content section, so those
need to be rearranged


```html
...

    <div id='article'>

        <div id='title'>
            <h1>
                Setup Blog
            </h1>
        </div>

        <div id='subtitle'>
            <h1>
                This is a blog post outlining the process of setting up a blog and hosting on my own website.
            </h1>
        </div>

        <h2>Markdown</h2>

        <p>It starts, naturally, with a markdown document:</p>

        <p>You are looking at a Markdown document.</p>

    </div>

...
```

We also need to change the title for our html document in the head:

```html
<!DOCTYPE html>
<html>

<head>
    <title>

        Setup Blog

    </title>

...
```

If there are any math sections, they may need to be changed:

```markdown

$$ Math $$  -> $$ Math $$ (unchanged)

Inline $ Math $ like this -> Inline \( Math \) like this

```
If there are any code sections they will need to be changed:

```markdown

\`\`\`c++
#include <iostream>

int main() {
  std::cout << "Hello World." << std::endl;
  return 0;
}\`\`\`\

<pre><code class="language-cpp">#include &lt;iostream&gt;

int main() {
  std::cout &lt;&lt; &ldquo;Hello World.&rdquo; &lt;&lt; std::endl;
  return 0;
} </code></pre>

```

Export
===============================================================================

Add the newest blog to the list of blogs at [Blog](/blog)

```
<div class='post'>
    <p class='post-title'><a href="/blogs/setupblog.html"> Setup Blog </a></span>
    <p class='post-date'> 17 March 2020 </span>
    <p class='post-subtitle'> A self documenting blog that explains how Trevor posts blogs to this website. </p>
</div>
```

Once the blog has been written, converted, and finalized, the last thing to do
is export:

```
trevord.black$ scp -r * <user>@trevord.black:<folder>
```

And that's it.

Just refresh the page.