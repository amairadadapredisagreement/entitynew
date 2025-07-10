.. _broken-link-building:

Broken Link Building: Hướng dẫn từng bước biến link hỏng thành cơ hội vàng
==========================================================================

.. figure:: https://ahrefs.com/blog/wp-content/uploads/2021/01/broken-link-building.png
   :alt: Broken Link Building Process
   :width: 800
   :align: center
   :target: https://ahrefs.com/blog/broken-link-building/

   *Hình 1: Quy trình Broken Link Building hiệu quả (Nguồn: Ahrefs)*

Theo nghiên cứu từ `Moz <https://moz.com/blog/broken-link-building>`_, **89% website** có ít nhất 1 broken link. Bài viết này sẽ hướng dẫn bạn khai thác triệt để cơ hội từ những link hỏng này, một chiến lược "mũ trắng" được `Google <https://developers.google.com/search/docs/advanced/guidelines/broken-links>`_ khuyến khích.

.. contents::
   :depth: 3
   :local:
   :backlinks: none

1. Cách tìm link gãy trên website lớn
-------------------------------------

### 1.1 Sử dụng công cụ miễn phí

.. code-block:: python
   :caption: Tìm broken link với Python
   :linenos:
   :emphasize-lines: 5-8

   import requests
   from bs4 import BeautifulSoup

   def find_broken_links(url):
       response = requests.get(url)
       soup = BeautifulSoup(response.text, 'html.parser')
       
       broken_links = []
       for link in soup.find_all('a'):
           href = link.get('href')
           if href and 'http' in href:
               try:
                   if requests.get(href).status_code == 404:
                       broken_links.append(href)
               except:
                   pass
       return broken_links

**Công cụ khác**:
- `Check My Links <https://chrome.google.com/webstore/detail/check-my-links/ojkcdipcgfaekbeaelaapakgnjflfglf>`_ (Extension Chrome)
- `W3C Link Checker <https://validator.w3.org/checklink>`_

### 1.2 Target website chất lượng

.. list-table:: Tiêu chí chọn website
   :widths: 30 70
   :header-rows: 1

   * - **Chỉ số**
     - **Giá trị tối thiểu**
   * - Domain Authority (DA)
     - ≥ 40
   * - Traffic
     - ≥ 10K/tháng
   * - Tỷ lệ link outbound
     - ≥ 20 link/trang

2. Tạo nội dung thay thế hoàn hảo
----------------------------------

### 2.1 Phân tích link gốc

.. raw:: html

   <div class="admonition note">
   <p class="admonition-title">Quy trình 4 bước</p>
   <ol>
   <li>Dùng <a href="https://web.archive.org/" target="_blank">Wayback Machine</a> xem nội dung cũ</li>
   <li>Phân tích anchor text và context xung quanh</li>
   <li>Xác định <strong>loại nội dung</strong> (blog post, infographic...)</li>
   <li>Đánh giá chất lượng (word count, depth...)</li>
   </ol>
   </div>

### 2.2 Công thức nội dung "đánh bại" bản gốc

.. math::
   Q_{new} = Q_{old} \times 1.5 + \Delta_{data} + \Delta_{media}

*Trong đó*:
- *Q<sub>new</sub>*: Chất lượng nội dung mới
- *Q<sub>old</sub>*: Chất lượng nội dung cũ
- *Δ<sub>data</sub>*: Giá trị gia tăng từ dữ liệu mới
- *Δ<sub>media</sub>*: Giá trị từ multimedia

3. Nghệ thuật outreach thành công
---------------------------------

### 3.1 Email template chuẩn

.. code-block:: text
   :caption: broken_link_outreach.txt
   :emphasize-lines: 3,6

   Chủ đề: Góp ý về broken link trên [Tên Website]

   Xin chào [Tên],

   Tôi vừa phát hiện link hỏng trên trang [URL trang]:
   - Link gãy: [URL link hỏng]
   - Anchor text: "[Text link]"

   Tôi có bài viết mới cập nhật về chủ đề này:
   - Tiêu đề: "[Tiêu đề bài của bạn]"
   - Nội dung: [Mô tả ngắn điểm nổi bật]
   - URL: [Link bài của bạn]

   Bạn có muốn thay thế link hỏng bằng bài viết này không?

   Cảm ơn,
   [Tên bạn]
   [Chức vụ]
   [Website]

### 3.2 Công cụ hỗ trợ

.. grid:: 1 1 2
   :gutter: 2

   .. grid-item-card::
      :text-align: center

      **Hunter.io**
      Tìm email chính xác
      `hunter.io <https://hunter.io/>`_

   .. grid-item-card::
      :text-align: center

      **Lemlist**
      Tự động hóa email
      `lemlist.com <https://lemlist.com/>`_

4. Case study thực tế
---------------------

**Ví dụ**: Thay thế broken link trên `Wikipedia`

.. csv-table:: Kết quả sau 3 tháng
   :file: data/broken_link_results.csv
   :widths: 40, 30, 30
   :header-rows: 1

*File data/broken_link_results.csv*:

.. code-block:: text
   :caption: broken_link_results.csv

   Chỉ số,Trước,Sau
   Referring domains,12,47
   Organic traffic,350/month,1,200/month
   Domain Authority,32,41

5. Lỗi cần tránh
----------------

.. admonition:: ⚠️ Cảnh báo quan trọng
   :class: danger

   - **Đừng** đề nghị thay thế khi chưa xem nội dung gốc
   - **Tránh** dùng anchor text thương mại ("mua sắm ngay")
   - **Không** spam cùng email cho nhiều người

6. Công cụ nâng cao
--------------------

.. tab-set::

   .. tab-item:: Miễn phí
      :sync: free

      - `Dead Link Checker <https://www.deadlinkchecker.com/>`_
      - `Google Search Console <https://search.google.com/search-console>`_

   .. tab-item:: Trả phí
      :sync: paid

      - `Ahrefs <https://ahrefs.com/>`_
      - `SEMrush <https://semrush.com/>`_

Kết luận
--------

.. grid:: 1 2 2
   :gutter: 3

   .. grid-item-card::
      :text-align: center

      **📈 Hiệu quả**
      - 73% tỷ lệ phản hồi
      - 5x referring domains

   .. grid-item-card::
      :text-align: center

      **⏳ Thời gian**
      - 2-3 tuần/chiến dịch
      - 15-20 email/ngày

.. raw:: html

   <div class="sd-card sd-mt-3">
   <div class="sd-card-header">
   <h3>Tài nguyên tham khảo</h3>
   </div>
   <div class="sd-card-body">
   <ul>
   <li><a href="https://ahrefs.com/blog/broken-link-building/" target="_blank">Ahrefs: Broken Link Building Guide</a></li>
   <li><a href="https://moz.com/blog/broken-link-building" target="_blank">Moz: The Advanced Guide</a></li>
   </ul>
   </div>
   </div>
