.. _backlink-guide:

Backlink là gì? Giải thích Toàn tập cho Người mới A-Z
=====================================================

.. figure:: https://moz.com/images/assets/features/why-are-backlinks-important-to-seo.png?auto=compress%2Cformat&fit=crop&dm=1700500599&s=1e717cdc3e322c33e79b697fcb13a253
   :alt: Minh họa backlink
   :width: 600
   :align: center

   *Hình 1: Mô hình backlink giữa các website (Nguồn: `Moz <https://moz.com>`_)*

**Backlink** (liên kết ngược) là yếu tố sống còn trong SEO. Bài viết này sẽ giải thích từ khái niệm cơ bản đến kỹ thuật nâng cao, với dẫn chứng từ các nguồn uy tín như `Google Search Central <https://developers.google.com/search/docs>`_, `Ahrefs <https://ahrefs.com/blog/what-are-backlinks/>`_ và `Backlinko <https://backlinko.com/>`_.

.. contents::
   :depth: 3
   :local:
   :backlinks: none

1. Định nghĩa Backlink
----------------------

Theo `Wikipedia <https://en.wikipedia.org/wiki/Backlink>`_:

> *"Backlink là liên kết từ website khác trỏ về trang của bạn, giống như **phiếu bầu** đánh giá độ uy tín."*

**Ví dụ mã HTML**:
.. code-block:: html
   :linenos:
   :emphasize-lines: 3

   <!-- Trên website example.com -->
   <p>
   Đọc hướng dẫn SEO tại 
   <a href="https://your-site.com/seo-guide" title="Hướng dẫn SEO">đây</a>.
   </p>

→ Đây là backlink **dofollow** từ example.com tới your-site.com.

2. Phân loại Backlink
---------------------

.. list-table:: Các loại backlink phổ biến
   :widths: 20 30 50
   :header-rows: 1

   * - **Loại**
     - **Thuộc tính**
     - **Ví dụ**
   * - *Editorial*
     - Tự nhiên
     - Liên kết trong bài báo (`NYTimes <https://www.nytimes.com>`_)
   * - *Guest Post*
     - Chủ động xây dựng
     - Bài viết khách trên blog uy tín
   * - *Nofollow*
     - ``rel="nofollow"``
     - Comment forum, Wikipedia

3. Tại sao Backlink quan trọng?
------------------------------

Theo nghiên cứu từ `Ahrefs <https://ahrefs.com/seo/backlinks>`_:

- :fa:`line-chart` **93.3%** trang top 1 Google có backlink
- :fa:`balance-scale` Backlink chiếm **~30%** yếu tố xếp hạng
- :fa:`rocket` Tăng **referral traffic** (lượt truy cập gián tiếp)

.. math::
   \text{Điểm chất lượng} = \frac{\sum \text{DA backlink}}{\text{Tổng backlink}}

*Trong đó: DA = Domain Authority (Moz)*

4. Cách kiểm tra Backlink
-------------------------

Sử dụng Python để phân tích cơ bản:

.. code-block:: python
   :caption: backlink_checker.py

   import requests
   from bs4 import BeautifulSoup

   def get_backlinks(url):
       """Lấy danh sách backlink từ URL"""
       try:
           response = requests.get(url)
           soup = BeautifulSoup(response.text, 'html.parser')
           return [a['href'] for a in soup.find_all('a', href=True)]
       except Exception as e:
           print(f"Lỗi: {e}")
           return []

   print(get_backlinks("https://example.com"))

5. 10 Chiến lược xây dựng Backlink
-----------------------------------

.. raw:: html

   <div class="admonition success">
   <p class="admonition-title">Thành công</p>
   <ol>
   <li><strong>Skyscraper Technique</strong> (Backlinko)</li>
   <li>Viết <em>guest post</em> chất lượng</li>
   <li>Tạo <strong>infographic</strong> chia sẻ</li>
   </ol>
   </div>

6. Công cụ hữu ích
-------------------

- `Ahrefs Backlink Checker <https://ahrefs.com/backlink-checker>`_
- `Google Search Console <https://search.google.com/search-console>`_
- `Moz Link Explorer <https://moz.com/link-explorer>`_

.. raw:: html

   <div class="admonition warning">
   <p class="admonition-title">Cảnh báo</p>
   <p>Tránh mua backlink hàng loạt - vi phạm <a href="https://support.google.com/webmasters/answer/66356" target="_blank">Google Webmaster Guidelines</a>.</p>
   </div>

7. Câu hỏi thường gặp
---------------------

.. dropdown:: **Backlink nofollow có giá trị không?**
   :animate: fade-in-slide-down

   Có! Theo `John Mueller (Google) <https://twitter.com/JohnMu/status/1108463056887439360>`_, nofollow vẫn gián tiếp hỗ trợ SEO.

.. dropdown:: **Bao nhiêu backlink là đủ?**
   
   Không có con số chính xác. `Moz khuyến nghị <https://moz.com/blog/how-many-links-is-too-many>`_ tập trung vào **chất lượng** hơn số lượng.

Kết luận
--------

**Backlink chất lượng** là yếu tố không thể thiếu để:

- :fa:`trophy` Xếp hạng cao trên Google
- :fa:`users` Mở rộng audience
- :fa:`shield-alt` Xây dựng thương hiệu

.. raw:: html

   <div style="background: #f8f9fa; padding: 15px; border-left: 4px solid #4CAF50; margin-top: 20px;">
   <h3>Tài liệu tham khảo</h3>
   <ul>
   <li><a href="https://moz.com/learn/seo/backlinks" target="_blank">Moz: Backlinks 101</a></li>
   <li><a href="https://developers.google.com/search/docs/advanced/guidelines/links" target="_blank">Google Link Schemes</a></li>
   <li><a href="https://www.semrush.com/blog/backlinks/" target="_blank">SEMrush: Backlink Guide</a></li>
   </ul>
   </div>
