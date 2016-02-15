---
layout: post
lang: ko
title: 예제 포스트
category: Example
excerpt: "Just about everything you'll need to style in the theme: headings, paragraphs, blockquotes, tables, code blocks, and more."
tags: [intro, beginner, jekyll, tutorial]
comments: true
---

여기 이미지를 포함한 포스트가 어떻게 보이는지에 대한 예제가 있습니다. 두 개나 세 개의 이미지를 반응형으로 옆으로 나오게 하고 싶으면 `figure` 를 적절한 `class`와 함께 사용하면 됩니다. 각 `figure`의 인스턴스는 자동으로 번호가 매겨지며, 캡션에 표시됩니다.

### Figure (이미지나 비디오)

#### 하나만 표시하기

<figure>
  <a href="http://farm9.staticflickr.com/8426/7758832526_cc8f681e48_b.jpg"><img src="http://farm9.staticflickr.com/8426/7758832526_cc8f681e48_c.jpg"></a>
  <figcaption><a href="http://www.flickr.com/photos/80901381@N04/7758832526/" title="Morning Fog Emerging From Trees by A Guy Taking Pictures, on Flickr">사진을 찍는 남자가 찍은 나무 사이로 보이는 안개, 플리커에서</a>.</figcaption>
</figure>

온갖 청춘 이 이 두기 교향악이다. 우리의 그들은 생생하며, 무엇을 봄바람을 용감하고 이성은 설산에서 사막이다. 청춘에서만 속에서 모래뿐일 뼈 웅대한 인생에 바로 두기 것이다. 있는 밝은 이상의 피고 청춘의 할지라도 웅대한 지혜는 봄바람이다. 어디 뭇 위하여서 있으며, 낙원을 바로 창공에 것이다. 희망의 역사를 이성은 아니더면, 만물은 속에서 아름다우냐? 보는 같으며, 인도하겠다는 이것이다. 인생에 청춘은 역사를 인생의 같이 위하여, 거선의 불어 황금시대다. 그것은 유소년에게서 같이, 꽃 그들의 위하여 가는 그러므로 것이다. 타오르고 대고, 청춘이 피부가 힘있다. 설레는 꽃이 인간의 전인 사라지지 수 대중을 하였으며, 쓸쓸하랴? 같으며, 얼음 능히 인간의 봄바람이다.

#### 두 개 보이기

두 개의 이미지를 나란히 보이게 하면서 같은 캡션을 공유하게 하고 싶으면 `half` 클래스를 사용하세요.

{% highlight html %}
<figure class="half">
    <a href="/images/image-filename-1-large.jpg"><img src="/images/image-filename-1.jpg"></a>
    <a href="/images/image-filename-2-large.jpg"><img src="/images/image-filename-2.jpg"></a>
    <figcaption>두 개의 이미지를 설명하는 캡션.</figcaption>
</figure>
{% endhighlight %}

그러면 아래와 같이 보입니다.

<figure class="half">
  <a href="http://placehold.it/1200x600.JPG"><img src="http://placehold.it/600x300.jpg"></a>
  <a href="http://placehold.it/1200x600.jpeg"><img src="http://placehold.it/600x300.jpg"></a>
  <figcaption>두 개의 이미지를 설명하는 캡션.</figcaption>
</figure>

#### 세 개 보이기

세 개의 이미지를 나란히 보이게 하면서 같은 캡션을 공유하게 하려면 `third` 클래스를 사용하세요.

{% highlight html %}
<figure class="third">
  <img src="/images/image-filename-1.jpg">
  <img src="/images/image-filename-2.jpg">
  <img src="/images/image-filename-3.jpg">
  <figcaption>세 개의 이미지를 설명하는 캡션.</figcaption>
</figure>
{% endhighlight %}

그러면 아래와 같이 보입니다.

<figure class="third">
  <img src="http://placehold.it/600x300.jpg">
  <img src="http://placehold.it/600x300.jpg">
  <img src="http://placehold.it/600x300.jpg">
  <figcaption>세 개의 이미지를 설명하는 캡션.</figcaption>
</figure>

