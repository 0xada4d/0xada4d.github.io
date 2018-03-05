<div class="category">
  <h2>Categories</h2>
  <ul class="sideBarTags">
    {% assign tags = (site.tags | sort:0) %}
    {% for tag in tags %}
    <li>
      <a href="{{ site.baseurl}}/tag/{{ tag[0] }}" data-toggle="tooltip" data-placement="right" title="{{ tag[1].size }}">
        <span>{{tag[0] }}</span></a></li>
    {% endfor %}
  </ul>
</div>