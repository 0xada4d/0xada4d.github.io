<div class="archive">
	<h2> Archives </h2>
	{% assign postGrouping = site.posts | group_by_exp:"post", "post.date | date '%B %Y'" %}
{% for postGroup in PostGrouping %}
	<h3>{{ postGroup.name }}</h3>
		<ul>
			{% for post in postGroup.items %}
			<li><a href="{{ post.url }}">{{ post.title }}</a></li>
			{% endfor %}
		</ul>
{% endfor %}
</div>