---
layout: default
---

<!-- ========================================== -->
<!-- PHẦN 1: BÀI GIỚI THIỆU CỐ ĐỊNH Ở TRANG CHỦ -->
<!-- ========================================== -->

# Terminal Access: The Hideous One

Chào mừng các Tri giả đến với The Hideous One. 

Đây là trang phân tích xàm của THO hay nhất mà các Tri giả chưa từng hay biết. The Hideous One chuyên đi **Phân tích các khía cạnh của thế giới Solaris một cách (xàm) chuyên môn và chuyên sâu.**

## Tri giả sẽ tìm thấy gì ở đây?

Thế giới Solaris-3 bao chứa rất nhiều khái niệm phức tạp và những câu chuyện nền bị chôn vùi. Trang chính là nơi sẽ tập trung vào các chủ đề về thế giới Wuthering Wave ấy như

*   **Chu kì Reverberation:** Nguồn gốc, hệ quả và cách nó hoạt động trong thế giới Solaris và vũ trụ Wuthering Wave.
*   **Giải mã Somnoire:** Somnoire, nơi mà mọi thứ không phải là thực tế
*   **Đặc tính khoa học và tính chất vật lý của các cá thể** Phân tích cơ chế vật lý và nguyên nhân hình thành nên thế giới này.

![Thumbnail](/assets/img/THO_thumb.jpg)
*Hình ảnh minh họa*

> "Lament đã biết tất cả thành những quy luật khác nhau thông qua cơ chế chung sóng, chỉ riêng trừ... **lực hấp dẫn**" 

Hy vọng THO này sẽ trở thành một chốn thông tin nho nhỏ, giúp những ai đam mê thế giới của Wuthering Waves có một cái nhìn sâu sắc và toàn diện hơn!

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
