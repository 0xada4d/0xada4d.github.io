
<div class="archive">
	<h1> Archives </h1>
	<hr>
	{% assign postGrouping = site.posts | group_by_exp:"post", "post.date | date: '%B %Y'" %}
{% for postGroup in postGrouping %}
	<h5>{{ postGroup.name }}</h5>
		<ul>
			{% for post in postGroup.items %}
			<li><a href="{{ post.url }}">{{ post.title }}</a></li>
			{% endfor %}
		</ul>
{% endfor %}
