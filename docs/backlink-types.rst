Các Dạng Backlink Thường Gặp Trong SEO
======================================

**Backlink** (liên kết ngược) là yếu tố quan trọng nhất trong xây dựng **authority website**. Bài viết này phân tích 7 loại backlink phổ biến nhất theo nghiên cứu từ `Ahrefs <https://ahrefs.com/blog/types-of-backlinks/>`_.

.. contents::
   :depth: 2
   :local:
   :backlinks: none

1. Editorial Links (Liên kết Tự nhiên)
--------------------------------------

*"Liên kết được chèn tự nhiên trong nội dung"* - `Moz <https://moz.com/learn/seo/backlinks>`_

- **Đặc điểm**:
  - Xuất hiện trong bài viết chất lượng
  - Không phải trả phí
  - Contextual (nằm trong ngữ cảnh phù hợp)

- **Ví dụ**:
  .. code-block:: html
     :emphasize-lines: 3

     <p>Các công cụ phân tích backlink như 
     <a href="https://example.com">SEMrush</a> 
     giúp đo lường hiệu quả SEO.</p>

2. Guest Post Links (Bài viết Khách)
-----------------------------------

.. list-table:: 
   :widths: 30 70
   :header-rows: 1

   * - **Ưu điểm**
     - **Rủi ro**
   * - Kiểm soát anchor text
     - Google Penalty nếu spam
   * - Xây dựng quan hệ
     - Cần disclosure theo `Google Guidelines <https://developers.google.com/search/docs/advanced/guidelines/paid-links>`_

3. Directory Links (Danh bạ)
---------------------------

**Chỉ nên dùng danh bạ chất lượng**:

- `DMoz <http://www.dmoz.org/>`_ (đã đóng)
- `Business.com <https://www.business.com/>`_
- `Yelp <https://www.yelp.com/>`_

.. warning::
   Tránh các directory tự động (auto-submission) vì có thể bị phạt theo `Google Update <https://www.searchenginejournal.com/google-news-updates/>`_.

4. Forum Links (Diễn đàn)
------------------------

Cách sử dụng an toàn:

.. code-block:: rst
   :caption: Ví dụ signature forum

   *John Doe*
   **Chuyên gia SEO** tại 
   `Website của tôi <https://example.com>`_

5. Social Media Links
--------------------

.. raw:: html

   <div class="admonition note">
   <p class="admonition-title">Lưu ý</p>
   <p>Links từ MXH thường là <strong>nofollow</strong> nhưng vẫn có giá trị referral traffic.</p>
   </div>

6. Resource Links
----------------

**Ví dụ**:
- Bài viết "50 Công cụ SEO tốt nhất 2023"
- Danh sách resource pages

7. Paid Links (Liên kết Trả phí)
--------------------------------

.. danger::
   Vi phạm `Nguyên tắc quản trị trang web của Google <https://support.google.com/webmasters/answer/66356>`_. 
   Cần đánh dấu ``rel="sponsored"``.

Script Kiểm tra Backlink
------------------------

.. code-block:: python
   :caption: Kiểm tra loại backlink bằng Python

   import requests
   from urllib.parse import urlparse

   def analyze_backlink(url):
       try:
           response = requests.get(url)
           if 'sponsored' in response.text:
               return "PAID LINK"
           elif 'nofollow' in response.text:
               return "NOFOLLOW"
           else:
               return "DOFOLLOW"
       except:
           return "UNKNOWN"

   print(analyze_backlink("https://example.com"))

Kết luận
--------

Theo nghiên cứu từ `Backlinko <https://backlinko.com/link-building>`_:

- :fa:`check-circle` **Tốt nhất**: Editorial + Resource links
- :fa:`exclamation-triangle` **Cẩn thận**: Paid + Directory links
- :fa:`share-alt` **Bổ sung**: Social + Forum links

.. raw:: html

   <div style="background: #f8f9fa; padding: 15px; border-left: 4px solid #4CAF50; margin-top: 20px;">
   <h3>Tài nguyên tham khảo</h3>
   <ul>
   <li><a href="https://moz.com/beginners-guide-to-seo/how-search-engines-operate" target="_blank">Moz: How Search Engines Work</a></li>
   <li><a href="https://www.semrush.com/blog/backlink-analysis/" target="_blank">SEMrush: Backlink Analysis Guide</a></li>
   </ul>
   </div>
