# Archives
___
<div class="archive">
	{% assign postGrouping = site.posts | group_by_exp:"post", "post.date | date: '%B %Y'" %}
{% for postGroup in postGrouping %}
	<h3>{{ postGroup.name }}</h3>
		<ul>
			{% for post in postGroup.items %}
			<li><a href="{{ post.url }}">[{{ post.tag }}] {{ post.title }}</a></li>
			{% endfor %}
		</ul>
{% endfor %}
