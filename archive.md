<div class="archive">
	{% for post in site.posts %}
		{% assign currentDate = post.date | date: "%B %Y" %}
		{% if currentDate != myDate %}
           {% unless forloop.first %}</ul>{% endunless %}
           <h2>{{ currentDate }}</h2>
           <ul>
           {% assign myDate = currentDate %}
       {% endif %}
       <li><a href="{{ post.url }}"><span>{{ post.title }}</a></li>
       {% if forloop.last %}</ul>{% endif %}
   {% endfor %}

</div>