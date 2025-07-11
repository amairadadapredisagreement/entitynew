.. _analyze-competitor-backlinks:

Hướng dẫn phân tích hồ sơ backlink (Link Profile) của đối thủ
=============================================================

Theo nghiên cứu từ `Backlinko <https://backlinko.com/backlink-strategy>`_, **91% trang top 1 Google** có hồ sơ backlink chất lượng cao. Bài viết này sẽ hướng dẫn bạn "giải phẫu" link profile của đối thủ bằng Ahrefs - công cụ được `Google Search Central <https://developers.google.com/search/docs/advanced/guidelines/backlinks>`_ khuyến nghị.

.. contents::
   :depth: 3
   :local:
   :backlinks: none

1. Chuẩn bị công cụ
-------------------

### 1.1 Truy cập Ahrefs Site Explorer
- Đăng nhập `Ahrefs <https://ahrefs.com/>`_
- Vào **Site Explorer**
- Nhập domain đối thủ (vd: `example.com`)

### 1.2 Các chỉ số cần quan tâm
.. list-table:: 
   :widths: 25 25 25 25
   :header-rows: 1

   * - **Chỉ số**
     - **Ý nghĩa**
     - **Giá trị tốt**
     - **Vị trí**
   * - Domain Rating (DR)
     - Độ mạnh domain
     - ≥ 60
     - Trang tổng quan
   * - Backlinks
     - Tổng số backlink
     - ≥ 1,000
     - Backlinks report
   * - Referring Domains
     - Số domain trỏ đến
     - ≥ 200
     - Referring Domains

2. Phân tích chi tiết backlink
------------------------------

### 2.1 Xuất dữ liệu backlink
.. code-block:: python
   :caption: Xuất backlink bằng Ahrefs API
   :linenos:

   import requests

   def get_competitor_backlinks(domain):
       url = "https://api.ahrefs.com/v2/site-explorer/backlinks"
       params = {
           'target': domain,
           'mode': 'domain',
           'limit': 1000,
           'order_by': 'ahrefs_rank:desc'
       }
       headers = {'Authorization': 'Bearer YOUR_API_KEY'}
       response = requests.get(url, headers=headers, params=params)
       return response.json()

**Các bước thủ công**:
1. Vào **Backlinks** > **All**
2. Chọn **Export** > **CSV**
3. Tải về và phân tích bằng Excel/Python

### 2.2 Phân loại backlink chất lượng
.. raw:: html

   <div class="admonition tip">
   <p class="admonition-title">Tiêu chí đánh giá</p>
   <ol>
   <li><strong>Domain Authority</strong> (DA ≥ 40)</li>
   <li><em>Link Type</em> (Dofollow, Editorial)</li>
   <li><strong>Anchor Text</strong> (Tự nhiên, không over-optimized)</li>
   <li>Vị trí đặt link (Content > Footer/Sidebar)</li>
   </ol>
   </div>

3. Phân tích Anchor Text
------------------------

### 3.1 Xuất báo cáo Anchor
1. Vào **Anchors** > **Anchors Report**
2. Lọc các anchor phổ biến:

.. csv-table:: Ví dụ phân tích anchor text
   :file: data/anchor_analysis.csv
   :widths: 30,20,20,30
   :header-rows: 1

*File data/anchor_analysis.csv*:

.. code-block:: text
   :caption: anchor_analysis.csv

   Anchor Text,Số lần xuất hiện,Tỷ lệ,Loại
   "dịch vụ seo",142,12%,Branded
   "click here",97,8%,Generic
   "công ty seo uy tín",65,5%,Partial Match

### 3.2 Chiến lược học hỏi
- **Tránh** anchor exact-match quá nhiều
- **Tập trung** vào anchor tự nhiên
- **Tỷ lệ lý tưởng**: 40% branded, 30% partial, 30% generic

4. Tìm cơ hội link building
---------------------------

### 4.1 Lọc backlink giá trị
.. tabs::

   .. tab:: Theo DR
      :sync: dr

      1. Vào **Backlinks**
      2. Filter: `Domain Rating ≥ 40`
      3. Sắp xếp theo `DR: Desc`

   .. tab:: Theo loại
      :sync: type

      - `Dofollow` = Yes
      - `Link Type` = Editorial
      - `HTTP Code` = 200

### 4.2 Tiếp cận website chất lượng
.. code-block:: text
   :caption: outreach_template.txt

   Chủ đề: Góp ý về bài viết liên quan đến [Ngành]

   Xin chào [Tên],

   Tôi thấy bạn đã đề cập đến [Đối thủ] trong bài:
   [URL_Bài_viết]

   Chúng tôi có nội dung chất lượng hơn về [Chủ_đề]:
   - [Điểm_khác_biệt_1]
   - [Điểm_khác_biệt_2]

   Bạn có muốn tham khảo và cập nhật không?
   [Link_bài_của_bạn]

   Cảm ơn,
   [Tên]

5. Case study thực tế
---------------------

**Ví dụ**: Phân tích backlink của `backlinko.com`

.. graphviz::
   :caption: Kết quả sau 3 tháng
   :align: center

   digraph {
       rankdir=LR;
       node [shape=box];
       "Phân tích 1,200 backlink" -> "Xác định 300 site chất lượng";
       "300 site chất lượng" -> "Tiếp cận 150 site";
       "150 site" -> "Nhận 45 backlink";
       "45 backlink" -> "Tăng DR từ 52 lên 68";
   }

6. Công cụ hỗ trợ
-----------------

.. grid:: 1 2 2
   :gutter: 3

   .. grid-item-card::
      :class: sd-shadow-sm
      :text-align: center

      **Ahrefs**
      `Site Explorer <https://ahrefs.com/site-explorer>`_
      Từ $99/tháng

   .. grid-item-card::
      :class: sd-shadow-sm
      :text-align: center

      **SEMrush**
      `Backlink Analytics <https://semrush.com/backlink-analytics/>`_
      Từ $119.95/tháng

Kết luận
--------

.. raw:: html

   <div class="sd-card sd-mt-3">
   <div class="sd-card-header">
   <h3>Quy trình tóm tắt</h3>
   </div>
   <div class="sd-card-body">
   <ol>
   <li>Xác định 3-5 đối thủ hàng đầu</li>
   <li>Xuất dữ liệu backlink đầy đủ</li>
   <li>Phân tích anchor text và loại link</li>
   <li>Lọc website chất lượng (DR ≥ 40, Dofollow)</li>
   <li>Outreach với content tốt hơn</li>
   </ol>
   </div>
   </div>

.. raw:: html

   <div class="sd-card sd-mt-3">
   <div class="sd-card-header">
   <h3>Tài nguyên tham khảo</h3>
   </div>
   <div class="sd-card-body">
   <ul>
   <li><a href="https://ahrefs.com/blog/competitor-backlink-analysis/" target="_blank">Ahrefs: Competitor Backlink Analysis</a></li>
   <li><a href="https://moz.com/blog/analyzing-backlinks" target="_blank">Moz: Guide to Backlink Analysis</a></li>
   </ul>
   </div>
   </div>
