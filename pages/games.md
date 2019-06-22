---
layout: default
title: Games
description: 最近感兴趣的游戏
keywords: games, 游戏
permalink: /games
---

<div class="games">
{% for game_type in site.data.game_types %}
    {% assign type = game_type.type %}
    {% assign not_empty = false %}
    {% for game in site.game %}
        {% if game.title == "Game template" %}
            {% continue %}
        {% endif %}
        {% if game.categories contains type %}
            {% assign not_empty = true %}
        {% endif %}
    {% endfor %}
    
    {% if not_empty %}
    <h4>{{ type }}</h4>
    <ul>
        {% for game in site.game %}
            {% if game.title == "Game template" %}
                {% continue %}
            {% endif %}
            {% if game.categories contains type %}
                <li>
                    <a href="{{site.url}}{{game.url}}">{{ game.title }}</a>
                </li>
            {% endif %}
        {% endfor %}
    </ul>
    {% endif %}
{% endfor %}
<div>