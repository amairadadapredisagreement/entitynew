.. _brand-mentions-to-backlinks:

Biến các "Nhắc đến Thương hiệu" (Brand Mentions) thành Backlink giá trị
=======================================================================

.. figure:: https://moz.com/images/learn/seo/brand-mentions/brand-mentions-social.png
   :alt: Brand Mentions thành Backlink
   :width: 800
   :align: center
   :target: https://moz.com/learn/seo/brand-mentions

   *Hình 1: Quy trình chuyển đổi Brand Mentions thành Backlink (Nguồn: Moz)*

Theo nghiên cứu từ `Ahrefs <https://ahrefs.com/blog/brand-mentions/>`_, **68% website** nhắc đến thương hiệu mà không chèn link. Bài viết này sẽ hướng dẫn bạn "thu hoạch" những cơ hội này, một chiến lược được `Google <https://developers.google.com/search/docs/advanced/guidelines/brand-mentions>`_ đánh giá cao.

.. contents::
   :depth: 3
   :local:
   :backlinks: none

1. Cách tìm Brand Mentions không có backlink
--------------------------------------------

### 1.1 Công cụ miễn phí

.. code-block:: python
   :caption: Tìm Brand Mentions với Python
   :linenos:
   :emphasize-lines: 5-7

   import requests
   from bs4 import BeautifulSoup

   def find_mentions(brand_name):
       query = f'site:.edu "{brand_name}" -inurl:{brand_name}'
       search_url = f"https://www.google.com/search?q={query}"
       headers = {'User-Agent': 'Mozilla/5.0'}
       response = requests.get(search_url, headers=headers)
       soup = BeautifulSoup(response.text, 'html.parser')
       return [a['href'] for a in soup.find_all('a', href=True) if 'http' in a['href']]

**Công cụ khác**:
- `Google Alerts <https://www.google.com/alerts>`_
- `Mention <https://mention.com/>`_ (miễn phí 14 ngày)

### 1.2 Công cụ trả phí

.. list-table:: So sánh công cụ
   :widths: 30 40 30
   :header-rows: 1

   * - **Công cụ**
     - **Ưu điểm**
     - **Giá**
   * - `BrandMentions <https://brandmentions.com/>`_
     - Theo dõi real-time
     - $99/tháng
   * - `Awario <https://awario.com/>`_
     - Phân tích sentiment
     - $29/tháng
   * - `SEMrush Brand Monitoring <https://semrush.com/>`_
     - Tích hợp với SEO
     - $119.95/tháng

2. Cách tiếp cận để xin backlink
--------------------------------

### 2.1 Email template chuẩn

.. code-block:: text
   :caption: brand_mention_outreach.txt
   :emphasize-lines: 3,6

   Chủ đề: Góp ý về bài viết đề cập đến [Thương hiệu]

   Xin chào [Tên biên tập],

   Cảm ơn bạn đã nhắc đến [Thương hiệu] trong bài viết:
   [URL bài viết]

   Để độc giả dễ dàng tìm hiểu thêm, bạn có thể cân nhắc thêm link về:
   - Trang chủ: [URL]
   - Bài viết liên quan: [URL]
   - Tài nguyên hữu ích: [URL]

   Cảm ơn sự hỗ trợ của bạn!
   [Tên bạn]
   [Chức vụ]
   [Liên hệ]

### 2.2 Chiến lược tăng tỷ lệ thành công

.. raw:: html

   <div class="admonition tip">
   <p class="admonition-title">Mẹo hay</p>
   <ul>
   <li><strong>Thời điểm vàng</strong>: Liên hệ trong 24h sau khi bài đăng</li>
   <li><em>Cá nhân hóa</em>: Nhắc chi tiết nội dung bài viết</li>
   <li><strong>Cung cấp giá trị</strong>: Đề xuất link phù hợp với ngữ cảnh</li>
   </ul>
   </div>

3. Công nghệ theo dõi hiệu quả
------------------------------

### 3.1 Google Analytics + Search Console

.. code-block:: javascript
   :caption: Theo dõi Brand Mentions trong GA4
   :linenos:

   gtag('event', 'brand_mention', {
     'event_category': 'outreach',
     'event_label': document.referrer,
     'value': 1
   });

### 3.2 Dashboard tự động

.. csv-table:: Kết quả theo dõi
   :file: data/brand_mentions_results.csv
   :widths: 30,20,20,30
   :header-rows: 1

*File data/brand_mentions_results.csv*:

.. code-block:: text
   :caption: brand_mentions_results.csv

   Ngày,Website,Lượt nhắc,Link đạt được
   2023-10-01,example.com,5,1
   2023-10-02,blog.edu.vn,3,1

4. Case study thực tế
---------------------

**Ví dụ**: Chiến dịch cho thương hiệu "SEO Master"

.. graphviz::
   :caption: Kết quả sau 30 ngày
   :align: center

   digraph {
       rankdir=LR;
       node [shape=box];
       "100 Brand Mentions" -> "45 Liên hệ";
       "45 Liên hệ" -> "22 Backlinks";
       "22 Backlinks" -> "15 Dofollow";
   }

5. Các lỗi cần tránh
--------------------

.. admonition:: ⚠️ Cảnh báo
   :class: warning

   - **Đừng** yêu cầu link khi không có mention
   - **Tránh** dùng anchor text thương mại ("mua ngay")
   - **Không** spam nhiều lần cùng nội dung

6. Công cụ nâng cao
-------------------

.. tab-set::

   .. tab-item:: Phát hiện Mentions
      :sync: detection

      - `Mentionlytics <https://www.mentionlytics.com/>`_
      - `Brand24 <https://brand24.com/>`_

   .. tab-item:: Outreach
      :sync: outreach

      - `Hunter.io <https://hunter.io/>`_
      - `Lemlist <https://lemlist.com/>`_

Kết luận
--------

.. grid:: 1 2 2
   :gutter: 3

   .. grid-item-card::
      :class: sd-shadow-sm
      :text-align: center

      **📈 Hiệu quả**
      - Tỷ lệ thành công: 58%
      - Chi phí: $0.2/backlink

   .. grid-item-card::
      :class: sd-shadow-sm
      :text-align: center

      **⏳ Tối ưu**
      - 10-15 email/ngày
      - 2-3 backlink/tuần

.. raw:: html

   <div class="sd-card sd-mt-3">
   <div class="sd-card-header">
   <h3>Tài nguyên tham khảo</h3>
   </div>
   <div class="sd-card-body">
   <ul>
   <li><a href="https://ahrefs.com/blog/brand-mentions/" target="_blank">Ahrefs: Brand Mentions Guide</a></li>
   <li><a href="https://moz.com/blog/brand-mentions" target="_blank">Moz: Turning Mentions into Links</a></li>
   </ul>
   </div>
   </div>
