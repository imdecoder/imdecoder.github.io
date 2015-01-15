<article>
    <h3>
    {% if post.external-url %}
    <a title="{{ post.title }}" rel="bookmark" href="{{ post.url }}" class="permalink icon-link"></a>
    <a href="{{ post.external-url }}" title="{{ post.title }}" class="postTitle">{{ post.title }}</a>
    {% else %}
    <a href="{{ post.url }}" title="{{ post.title }}" class="postTitle shiftTitle" rel="bookmark">{{ post.title }}</a>
    {% endif %}
    <time datetime="{{ post.date | date:"%Y-%m-%d" }}" class="meta">{{ post.date | date:"%d %B %Y" }}</time>
    </h3>

    {% assign show= include.param %}

    {% case show %}

      {% when 'full' %}
          <section class="postMeta">
          {% if post.tags %}
          <span class="tags">
            <i class="icon-tag add-on"></i>
            {% for tag in post.tags %}
            <a href="/tags.html#{{ tag }}" title="{{ tag }}">{{ tag }}</a>&nbsp;
            {% endfor %}
          </span>
          {% endif %}
        </section>

        {{ post.content }}

      {% when 'excerpt' %}
          <section class="postMeta">
          {% if post.tags %}
          <span class="tags">
            <i class="icon-tag add-on"></i>
            {% for tag in post.tags %}
            <a href="/tags.html#{{ tag }}" title="{{ tag }}">{{ tag }}</a>&nbsp;
            {% endfor %}
          </span>
          {% endif %}
        </section>

        {{ post.excerpt }}

        <a href="{{ post.url }}">read more</a>
    {% endcase %}
</article>