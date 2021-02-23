---
layout: default
title: RSS Feed
permalink: /podcast-rss/
---

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rss version="2.0" xmlns:itunes="http://www.itunes.com/dtds/podcast-1.0.dtd" xmlns:content="http://purl.org/rss/1.0/modules/content/">
<channel>
    <title>{{ site.title | xml_escape }}</title>
    <link>{{ site.url | xml_escape }}</link>
    <language>en-us</language>
    <copyright>&#169; {{ "now" | date: "%Y" }} Jacob Campbell</copyright>
    <itunes:author>Locus of Transformation</itunes:author>
    <description>
        <![CDATA[
        <h3 class="text-center">{{ site.hostname | markdownify }}</h3>
        {{ site.description | markdownify }}
        ]]>
    </description>
    <itunes:type>episodic</itunes:type>
    <itunes:owner>
        <itunes:name>Jacob Campbell</itunes:name>
        <itunes:email>jacob.r.campbell@gmail.com</itunes:email>
    </itunes:owner>
    <itunes:image
        href="{{ site.url }}/assets/src/show-art.jpg"
    />
    <itunes:category text="Society &amp; Culture">
        <itunes:category text="Personal Journals"/>
    </itunes:category>
    <itunes:explicit>false</itunes:explicit>
    {%- for post in site.posts -%}
&#x20;    
    <item>
        <itunes:episodeType>{{ post.episode_type }}</itunes:episodeType>
        <itunes:episode>{{ post.itunes_episode }}</itunes:episode>
        <itunes:season>{{ post.itunes_season }}</itunes:season>
        <itunes:title>{{ post.title | xml_escape }}</itunes:title>
        <description>
            <![CDATA[
            <p>View <a href="{{ site.url }}{{ post.url }}">Episode {{ post.itunes_episode }}: {{ post.title }}</a>
            {{ post.excerpt | markdownify }}
            {{ post.content | markdownify }}
            ]]>
        </description>
        <enclosure 
        length="{{ post.enclosure_length_bytes }}" 
        type="audio/mpeg" 
        url="{{ post.enclosure_url | xml_escape }}"
        />
        <guid>season-{{ post.itunes_season }}--episode-{{ post.itunes_episode }}</guid>
        <link>{{ site.url }}{{ post.url }}</link>
    {%- if post.itunes_image_url -%}
        <itunes:image href="{{ site.url }}{{ post.itunes_image_url }}" />
    {%- endif -%}
        <pubDate>{{ post.date | date_to_rfc822 }}</pubDate>
        <itunes:duration>{{ post.itunes_duration_seconds }}</itunes:duration>
        <itunes:explicit>{{ post.itunes_explicit}}</itunes:explicit>
        <itunes:block>{{ post.itunes_block }}</itunes:block>
    </item>
{%- endfor -%}

</channel>
</rss>
```