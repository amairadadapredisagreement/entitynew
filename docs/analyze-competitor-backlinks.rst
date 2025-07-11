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
   :emphasize-lines: 3,6,9

   import requests

   def get_competitor_backlinks(domain):
       """Lấy danh sách backlink từ API Ahrefs"""
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

1. Đăng nhập `Ahrefs <https://ahrefs.com/>`_
2. Vào **Site Explorer** > Nhập domain đối thủ
3. Chọn tab **Backlinks** > **All**
4. Nhấn **Export** > Chọn **CSV**
5. Tải về và phân tích bằng Excel/Python

### 2.2 Phân loại backlink chất lượng

.. admonition:: 🔍 Tiêu chí đánh giá backlink chất lượng
   :class: tip

   .. list-table::
      :widths: 30 70
      :header-rows: 0

      * - **Domain Authority**
        - Chọn site có DA ≥ 40 (kiểm tra bằng `MozBar <https://moz.com/products/pro/seo-toolbar>`_)
      * - **Link Type**
        - Ưu tiên: *Dofollow*, *Editorial*, *Contextual*
      * - **Anchor Text**
        - Tự nhiên, không spam (tỷ lệ branded ≥ 40%)
      * - **Vị trí đặt link**
        - Trong nội dung > Sidebar/Footer

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

.. tab-set::

   .. tab-item:: Theo chỉ số DR
      :sync: dr

      1. Truy cập **Site Explorer** > **Backlinks**
      2. Sử dụng bộ lọc:
         - ``Domain Rating ≥ 40``
         - ``First seen: Last 6 months``
      3. Sắp xếp theo ``DR: Descending``
      4. Xuất danh sách (CSV/Excel)

   .. tab-item:: Theo loại link
      :sync: type

      - ✅ ``Dofollow = Yes``
      - ✏️ ``Link Type = Editorial``
      - 🟢 ``HTTP Code = 200``
      - 🚫 ``Link Type ≠ Sponsored/UGC``
      - 📌 ``Position = In content``

### 4.2 Chiến lược tiếp cận

**Email template** (tỷ lệ phản hồi cao):

.. code-block:: text
   :caption: outreach_template.txt
   :linenos:
   :emphasize-lines: 3,7,10

   Chủ đề: Gợi ý tài nguyên [Chủ đề] chất lượng hơn

   Xin chào [Tên biên tập],

   Tôi là [Tên bạn] từ [Công ty]. Tôi đánh giá cao bài viết của bạn:
   "[Tiêu đề bài viết]" ([URL])

   Chúng tôi vừa xuất bản nội dung cập nhật về [Chủ đề] với:
   - [Điểm khác biệt 1]: Dữ liệu nghiên cứu mới nhất 2024
   - [Điểm khác biệt 2]: Hướng dẫn từng bước chi tiết
   - [Điểm khác biệt 3]: Case study thực tế

   Bạn có thể xem tại: [URL bài viết của bạn]

   Nếu thấy phù hợp, bạn có thể cân nhắc thêm link tham khảo cho độc giả.

   Cảm ơn và mong nhận được phản hồi!
   [Tên đầy đủ]
   [Chức vụ]
   [Email/SĐT]
   [Website]

**Công cụ hỗ trợ**:
- `Hunter.io <https://hunter.io/>`_ (tìm email)
- `Mailchimp <https://mailchimp.com/>`_ (quản lý chiến dịch)
- `Streak <https://www.streak.com/>`_ (theo dõi email)

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
