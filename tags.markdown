---
title: tags
layout: page
---
<div id="tag_cloud">
{% for tag in site.tags %}
	<a href="#{{ tag[0] }}" title="{{ tag[0] }}" rel="{{ tag[1].size }}">{{ tag[0] }}</a>
{% endfor %}
</div>

<ul class="listing">
{% for tag in site.tags %}
	<li class="listing-seperator" id="{{ tag[0] }}">{{ tag[0] }}</li>
	{% for post in tag[1] %}
		<li class="listing-item">
			<time datetime="{{ post.date | date:"%Y-%m-%d" }}">{{ post.date | date:"%Y-%m-%d" }}</time>
			<a href="{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a>
		</li>
	{% endfor %}
{% endfor %}
</ul>

<script src="/media/js/jquery.tagcloud.js" type="text/javascript" charset="utf-8"></script> 
<script language="javascript">
	$.fn.tagcloud.defaults = {
		size:  {start:10, end:15, unit:'em'}
		color: {start:'#CDE', end:'#F52'}
	};

	$(function(){
		$('#tag_cloud a').tagcloud();
	});
</script>














