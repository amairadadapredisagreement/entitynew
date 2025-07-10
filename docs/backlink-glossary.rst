.. _backlink-glossary:

Tổng hợp các thuật ngữ Backlink quan trọng phải biết
====================================================

.. figure:: https://moz.com/images/learn/seo/glossary/seo-glossary-illustration.png
   :alt: Thuật ngữ SEO
   :width: 700
   :align: center
   :target: https://moz.com/learn/seo/glossary

   *Hình 1: Bộ thuật ngữ SEO cần thiết (Nguồn: `Moz Glossary <https://moz.com/learn/seo/glossary>`_)*

Theo nghiên cứu từ `Ahrefs <https://ahrefs.com/blog/seo-terms/>`_, việc hiểu rõ các thuật ngữ backlink giúp **tăng 68% hiệu quả** chiến dịch SEO. Dưới đây là 25 khái niệm quan trọng nhất được giải thích chi tiết, kèm ví dụ minh họa và công cụ kiểm tra.

.. contents::
   :depth: 3
   :local:
   :backlinks: none

1. Các chỉ số đánh giá
---------------------

.. glossary::
   :sorted:

   Domain Authority (DA)
      **Định nghĩa**: Chỉ số từ 0-100 của Moz đo *sức mạnh tổng thể* tên miền. 
      
      **Công thức tính**:
      .. math::
         DA = \frac{\log(TF) \times CF}{R} \times 10
      
      *Trong đó*:
        - *TF*: Tổng backlink chất lượng
        - *CF*: Citation Flow
        - *R*: Hệ số điều chỉnh

      **Tool**: `Moz Link Explorer <https://moz.com/link-explorer>`_

   Page Authority (PA)
      Tương tự DA nhưng áp dụng cho *từng trang cụ thể*. Theo `Moz <https://moz.com/learn/seo/page-authority>`_, PA quan trọng hơn DA khi đánh giá backlink.

   Trust Flow (TF)
      Chỉ số từ Majestic SEO đo độ *tin cậy* của backlink dựa trên liên kết từ các site uy tín (`.edu`, `.gov`, báo chí).

   Citation Flow (CF)
      Đo *lượng* backlink không quan tâm chất lượng. TF/CF > 0.5 được coi là tốt.

2. Loại backlink
---------------

.. list-table:: So sánh backlink chất lượng và độc hại
   :widths: 25 35 40
   :header-rows: 1

   * - **Thuật ngữ**
     - **Mô tả**
     - **Ví dụ**
   * - *Editorial Link*
     - Liên kết tự nhiên trong nội dung
     - Bài báo giới thiệu sản phẩm
   * - *Guest Post Link*
     - Link trong bài viết khách
     - Blog tiếp thị đăng bài PR
   * - *Toxic Backlink*
     - Link từ site spam, bị phạt
     - Site casino, khiêu dâm
   * - *PBN (Private Blog Network)*
     - Mạng blog riêng để xây backlink
     - 50 site vệ tinh cùng chủ sở hữu
   * - *Link Farm*
     - Trang chứa toàn outbound links
     - Directory tự động

3. Kỹ thuật xây dựng
--------------------

.. glossary::

   Link Profile
      **Tổng thể** backlink của website, bao gồm:
      
      .. code-block:: python
         :caption: Phân tích link profile

         def analyze_profile(url):
             metrics = {
                 'dofollow': 0,
                 'nofollow': 0,
                 'sponsored': 0,
                 'toxic': check_toxicity(url)
             }
             return metrics

   Link Juice
      *Sức mạnh* được truyền qua backlink. Tính bằng:

      .. math::
         Juice = \frac{PA_{source}}{Links_{out}}

   Anchor Text
      Chữ hiển thị của liên kết. Phân loại:

      - *Exact Match*: "dịch vụ SEO"
      - *Partial Match*: "công ty dịch vụ SEO"
      - *Branded*: "Moz"
      - *Generic*: "tại đây"

4. Công cụ & Thuật ngữ kỹ thuật
-------------------------------

.. tabs::

   .. tab:: Công cụ phân tích

      - `Ahrefs Site Explorer <https://ahrefs.com/site-explorer>`_
      - `Majestic SEO <https://majestic.com>`_
      - `Google Search Console <https://search.google.com/search-console>`_

   .. tab:: Thuật ngữ nâng cao

      .. glossary::

         Disavow
            Công cụ của Google để *từ chối* backlink xấu. Ví dụ file:

            .. code-block:: text
               :caption: disavow.txt

               # Liên kết từ spam site
               domain:spam-site.com
               https://spam-site.com/bad-page.html

         Link Sculpting
            Kỹ thuật điều hướng *link juice* bằng `rel="nofollow"`.

         Broken Link Building
            Tìm link hỏng trên site khác và đề xuất thay bằng link của bạn.

5. Bảng tra cứu nhanh
---------------------

.. csv-table:: Chỉ số lý tưởng theo ngành
   :file: data/backlink-metrics.csv
   :widths: 20, 20, 20, 20, 20
   :header-rows: 1

*File CSV mẫu*:

.. code-block:: text
   :caption: backlink-metrics.csv

   Ngành,DA tối thiểu,TF tối thiểu,Tỷ lệ Dofollow,Số referring domains
   Thương mại điện tử,35,15,60%,150+
   Du lịch,30,12,55%,100+
   Công nghệ,40,20,65%,200+

6. Script kiểm tra backlink
--------------------------

.. code-block:: python
   :caption: backlink_analyzer.py

   import requests
   from bs4 import BeautifulSoup

   def check_backlink(url):
       """Phân tích backlink tự động"""
       try:
           response = requests.get(url)
           soup = BeautifulSoup(response.text, 'html.parser')
           
           return {
               'dofollow': len(soup.find_all('a', rel=False)),
               'nofollow': len(soup.find_all('a', rel='nofollow')),
               'anchors': [a.text for a in soup.find_all('a')]
           }
       except Exception as e:
           return {'error': str(e)}

   print(check_backlink("https://example.com"))

7. Thuật ngữ mở rộng
--------------------

.. glossary::

   Link Equity
      Giá trị tổng hợp từ các backlink truyền đến trang.

   Link Bait
      Nội dung được tạo ra *mục đích* thu hút backlink tự nhiên.

   Deep Link
      Liên kết trỏ đến trang con thay vì trang chủ.

   Link Graph
      Sơ đồ mối quan hệ liên kết giữa các trang web.

Tài nguyên tham khảo
--------------------

.. raw:: html

   <div class="references" style="background: #f8f9fa; padding: 20px; border-radius: 5px;">
   <h3>Nguồn uy tín</h3>
   <ul>
   <li><a href="https://moz.com/learn/seo" target="_blank">Moz SEO Learning Center</a></li>
   <li><a href="https://developers.google.com/search/docs" target="_blank">Google Search Docs</a></li>
   <li><a href="https://ahrefs.com/blog/" target="_blank">Ahrefs Blog</a></li>
   <li><a href="https://backlinko.com/seo-terms" target="_blank">Backlinko Glossary</a></li>
   </ul>
   </div>

.. admonition:: Lưu ý quan trọng
   :class: warning

   Các chỉ số DA, PA, TF, CF chỉ mang tính *tham khảo tương đối*. Theo `John Mueller (Google) <https://twitter.com/JohnMu/status/1485958101942726656>`_, Google không sử dụng các chỉ số này để xếp hạng.
