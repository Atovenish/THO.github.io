---
layout: default
---

<!-- ========================================== -->
<!-- PHẦN 1: BÀI GIỚI THIỆU CỐ ĐỊNH Ở TRANG CHỦ -->
<!-- ========================================== -->

# Khởi động: Hành trình giải mã thế giới Wuthering Waves

Chào mừng các bạn đến với trạm dừng chân mới, nơi chúng ta sẽ cùng nhau bóc tách và đi sâu vào những bí ẩn kiến tạo nên thế giới của **Wuthering Waves**. 

Thay vì chỉ dừng lại ở các bài hướng dẫn build nhân vật hay tối ưu sát thương, blog này được sinh ra với một mục đích duy nhất: **Phân tích cấu trúc cốt truyện và lore (lịch sử thế giới) của game một cách hệ thống nhất.**

## Bạn sẽ tìm thấy gì ở đây?

Thế giới Solaris-3 bao chứa rất nhiều khái niệm phức tạp và những câu chuyện nền bị chôn vùi. Trong thời gian tới, blog sẽ tập trung vào các chủ đề chính sau:

*   **Hệ thống Thần thoại Roya:** Nguồn gốc, hệ quả và cách nó thao túng dòng chảy lịch sử của các vùng đất.
*   **Giải mã Aleph-1:** Cấu trúc thực sự đằng sau thực thể này là gì? Các giả thuyết về bản chất không gian và thời gian trong game.
*   **Hiện tượng Voidstorm (Bão Hư Không):** Phân tích cơ chế vật lý và nguyên nhân hình thành của những cơn bão tàn phá này.

![Bầu trời Solaris-3](/assets/img/THO_thumb.jpg)
*Hình ảnh minh họa*

> "Âm thanh là cội nguồn của vạn vật, nhưng cũng là thứ kết liễu tất cả." 

Hy vọng blog này sẽ trở thành một cuốn từ điển nhỏ, giúp những ai đam mê cốt truyện của Wuthering Waves có một cái nhìn sâu sắc và toàn diện hơn!

---

<!-- ========================================== -->
<!-- PHẦN 2: DANH SÁCH BÀI VIẾT (TỰ ĐỘNG CẬP NHẬT) -->
<!-- ========================================== -->

## Các bài phân tích mới nhất

<ul>
  {% for post in site.posts %}
    <li style="margin-bottom: 20px; list-style: none;">
      <!-- Hiển thị ảnh Thumbnail nếu có -->
      {% if post.thumbnail %}
        <img src="{{ post.thumbnail | relative_url }}" alt="{{ post.title }}" style="max-width: 200px; display: block; margin-bottom: 10px; border-radius: 8px;">
      {% endif %}
      
      <!-- Hiển thị Tiêu đề bài viết -->
      <h3>
        <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
      </h3>
      
      <!-- Hiển thị Ngày đăng -->
      <span style="color: gray; font-size: 0.9em;">{{ post.date | date: "%d/%m/%Y" }}</span>
      
      <!-- Trích dẫn ngắn của bài viết -->
      <p>{{ post.excerpt | strip_html | truncatewords: 20 }}</p>
    </li>
  {% endfor %}
</ul>
