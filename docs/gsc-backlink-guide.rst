.. _gsc-backlink-guide:

Cách sử dụng Google Search Console để theo dõi và quản lý Backlink
==================================================================

Theo báo cáo từ `Google Developers <https://developers.google.com/search/docs/advanced/guidelines/backlinks>`_, **Google Search Console (GSC)** là công cụ chính thức nhất để theo dõi backlink với dữ liệu trực tiếp từ chỉ mục của Google. Bài viết này sẽ hướng dẫn bạn khai thác triệt để tính năng này.

.. contents::
   :depth: 3
   :local:
   :backlinks: none

1. Truy cập báo cáo backlink trong GSC
--------------------------------------

### 1.1 Các bước cơ bản

.. code-block:: none
   :caption: Đường dẫn truy cập
   :linenos:

   1. Đăng nhập https://search.google.com/search-console
   2. Chọn property website
   3. Menu bên trái > Liên kết > Liên kết bên ngoài

### 1.2 Cấu trúc báo cáo

.. list-table:: Các thành phần chính trong báo cáo backlink
   :widths: 30 45 25
   :header-rows: 1
   :align: left

   * - **Mục**
     - **Ý nghĩa**
     - **Dữ liệu mẫu**
   * - Trang liên kết nhiều nhất
     - Các URL trên website của bạn nhận được nhiều backlink nhất
     - 1,245 liên kết
   * - Trang đích hàng đầu
     - Các URL được các backlink trỏ đến nhiều nhất
     - /blog/seo
   * - Trang web liên kết hàng đầu
     - Các domain bên ngoài trỏ backlink về website của bạn
     - example.com

2. Phân tích chi tiết từng mục
-------------------------------

### 2.1 Trang web liên kết hàng đầu
**Cách sử dụng**:
- Click vào từng domain để xem:
  - URL nguồn (trang chứa link)
  - URL đích (trang được trỏ đến)
  - Anchor text sử dụng

.. admonition:: 💡 Mẹo phân tích
   :class: tip

   - Tìm site có **Authority cao** (gov, edu, news)
   - Kiểm tra link **Dofollow/Nofollow** bằng:
     .. code-block:: python
        :caption: Kiểm tra link type

        import requests
        from bs4 import BeautifulSoup

        def check_link_type(url):
            res = requests.get(url)
            soup = BeautifulSoup(res.text, 'html.parser')
            return [a.get('rel') for a in soup.find_all('a') if 'href' in a.attrs]

### 2.2 Anchor text phổ biến
.. csv-table:: Ví dụ dữ liệu anchor
   :file: data/gsc_anchor.csv
   :widths: 40,30,30
   :header-rows: 1

*File data/gsc_anchor.csv*:
.. code-block:: text
   :caption: gsc_anchor.csv

   Anchor Text,Số lần xuất hiện,Tỷ lệ
   "dịch vụ SEO",142,12%
   "xem thêm",97,8%
   "tại đây",65,5%

3. Xuất dữ liệu từ GSC
----------------------

### 3.1 Xuất báo cáo thủ công
1. Trên giao diện GSC, chọn **Xuất báo cáo**
2. Chọn định dạng:
   - Google Sheets
   - CSV
   - Excel

### 3.2 Sử dụng API (nâng cao)
.. code-block:: python
   :caption: Lấy dữ liệu qua GSC API
   :linenos:
   :emphasize-lines: 6-9,14

   from google.oauth2 import service_account
   from googleapiclient.discovery import build

   # Xác thực
   credentials = service_account.Credentials.from_service_account_file(
       'service-account.json',
       scopes=['https://www.googleapis.com/auth/webmasters']
   )

   service = build('searchconsole', 'v1', credentials=credentials)

   # Lấy dữ liệu backlink
   response = service.sites().list().execute()
   links = service.externalLinks().list(siteUrl='sc-domain:example.com').execute()

   print(f"Tổng số backlink: {links['total']}")

4. Cảnh báo backlink xấu
------------------------

### 4.1 Dấu hiệu nhận biết
.. raw:: html

   <div class="admonition warning">
   <p class="admonition-title">Cảnh báo từ Google</p>
   <ul>
   <li>Link từ site <strong>spam/bán link</strong></li>
   <li>Anchor text <em>over-optimized</em> (ví dụ: "mua iPhone rẻ")</li>
   <li>Tỷ lệ link <strong>dofollow</strong> bất thường (>80%)</li>
   </ul>
   </div>

### 4.2 Cách xử lý
1. Vào **Bảo mật và quyền riêng tư** > **Liên kết ngược**
2. Tải file `disavow.txt` lên
3. Mẫu file:
   .. code-block:: text
      :caption: disavow.txt

      # Link xấu từ spam site
      domain:spam-site.com
      https://spam-site.com/bad-page.html

5. Case study thực tế
---------------------

**Ví dụ**: Tăng 120% backlink chất lượng sau 3 tháng

.. graphviz::
   :caption: Chiến lược thành công
   :align: center

   digraph {
       rankdir=LR;
       node [shape=box];
       "Phân tích GSC" -> "Xác định 50 site chất lượng";
       "50 site" -> "Viết content tốt hơn";
       "Content tốt" -> "Outreach 30 site";
       "Outreach" -> "Nhận 18 backlink";
   }

6. Công cụ bổ sung
------------------

.. grid:: 1 2 2
   :gutter: 3

   .. grid-item-card::
      :class: sd-shadow-sm
      :text-align: center

      **🔍 Kiểm tra backlink**
      - `Ahrefs Free Backlink Checker <https://ahrefs.com/backlink-checker>`_
      - `Ubersuggest <https://neilpatel.com/ubersuggest/>`_

   .. grid-item-card::
      :class: sd-shadow-sm
      :text-align: center

      **📈 Phân tích**
      - `Google Analytics <https://analytics.google.com>`_
      - `Data Studio <https://datastudio.google.com>`_

Kết luận
--------

.. rst-class:: highlight

**Google Search Console** là vũ khí mạnh nhất để:

- Theo dõi backlink **chính xác 100%** từ Google
- Phát hiện cơ hội **link building chất lượng**
- Cảnh báo sớm **backlink độc hại**

.. raw:: html

   <div class="sd-card sd-mt-3">
   <div class="sd-card-header">
   <h3>Tài nguyên tham khảo</h3>
   </div>
   <div class="sd-card-body">
   <ul>
   <li><a href="https://support.google.com/webmasters/answer/12976085" target="_blank">Hướng dẫn chính thức từ Google</a></li>
   <li><a href="https://moz.com/blog/google-search-console-backlinks" target="_blank">Moz: Khai thác GSC hiệu quả</a></li>
   </ul>
   </div>
   </div>
