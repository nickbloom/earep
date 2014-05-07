<html>
<head>
<title>Nick Bloom - Models, Models, Everwhere&#33;</title>
<link rel="stylesheet" href="rmd.css">
<script type="text/javascript" src="http://use.typekit.com/dkf3nhj.js"></script>
<script type="text/javascript">try{Typekit.load();}catch(e){}</script>
<script type="text/javascript">

  var _gaq = _gaq || [];
  _gaq.push(['_setAccount', 'UA-32178853-1']);
  _gaq.push(['_trackPageview']);

  (function() {
    var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
    ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
    var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
  })();

</script>
</head>

<body>


<div id="top">
<div id="topin">
<ul>
<li id="first"><a href="http://nickbloom.net">HOME</a></li>
<li><a href="work.html">WORK</a></li>
<li class="on"><a href="play.html">FUN</a></li>
<!--<li><a href="http://nickbloom.net/blog/">Blog</a></li>-->
<li><a href="vita.html">VITA</a></li>
<li><a href="contact.html">SAY HI</a></li>
</ul>
</div>
</div>
<div id="container">

# Embedded Altruism 2 - Appendix
## More Graphs!




### A Note on the Approach

Many of the graphs below are density plots of propensities, or predicted probabilities. These predicted probabilities are the predicted probabilities calculated by the model for each individual person, *not* the variability of a coefficient's effect *or* the marginal effect of a coefficient.

Instead, I am grouping predicted probabilites by independent variables, and summarizing those groups with densities. I see these density plots as a (very, very) rough estimation of the distribution of latent probability of donating blood within a given group (for example, the country of France). I can't be *sure* that grouping variables are responsible for the different distributions, or that differences between distributions are meaningful. However, I think the plots are useful heuristically to get a better feel for underlying differences in the Eurobarometer population, without making assumptions about the pdf of probability.

### Visualizing the Donor Population

First, let's get a sense of the overall population of donors in the sample:

![](figure/unnamed-chunk-2.png) 


Overall, people aren't very likely to donate blood; the bulk of the predicted probabilities are between 0.1 and 0.4. The vertical line is the mean of the propensities, which is ≈0.286. But, pooling the results like this is probably masking within-country variation. So, let's see how it looks by country:

![](figure/unnamed-chunk-3.png) 


This picture looks more realistic, with densities varying wildly by country. France, in particular, looks like a positive outlier, with most people likely to donate. Let's get a better look:

![](figure/unnamed-chunk-4.png) 


It looks like, on average, people from France are the most likely to give blood. The gray vertical line is the global mean propensity for countries other than France (≈0.272), and the vertical red line is the mean propensity for France (≈0.449). Just for comparison's sake, here are the country-level densities by estimation method:

![](figure/unnamed-chunk-5.png) 


What's interesting (to me at least) is that the country densities follow one of two patterns: 1) normally distributed, or 2) bimodal. The bi-modal countries are generally coastal Mediterranean countries, and probably more importantly, mostly blood bank countries. This complicates interpretation of mean propensities within countries, since it appears the mean is sometimes deceiving.

To get a sense of institutional effects, let's see what these densities look like by collection regime:

![](figure/unnamed-chunk-6.png) 

As predicted in the model, individuals nationally-run blood-collection systems are the most likely to donate, followed by Red Cross, and then Blood Banking regimes. Similarly, donor groups increase overally donation propensity:

![](figure/unnamed-chunk-7.png) 





### Comparisons of Model Fit

![](figure/unnamed-chunk-8.png) 


![](figure/unnamed-chunk-9.png) 


</div>

<div id="footer">
<p>All your blood are belong to us.</p>
</div>
</div>
<script type="text/javascript">

  var _gaq = _gaq || [];
  _gaq.push(['_setAccount', 'UA-37573172-1']);
  _gaq.push(['_setDomainName', 'nickbloom.net']);
  _gaq.push(['_setAllowLinker', true]);
  _gaq.push(['_trackPageview']);

  (function() {
    var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
    ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'http://www') + '.google-analytics.com/ga.js';
    var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
  })();

</script>
</body>
</html>



