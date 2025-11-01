# Changelog - Django 5.1 Compatibility Update

## Version 1.5.0 - Django 5.1 Compatibility

### Thay đổi chính

#### 1. Cập nhật API Django đã bị loại bỏ

**views.py:**
- ✅ Thay thế `ugettext_lazy` bằng `gettext_lazy` (Django 4.0+)
- ✅ Thay thế `request.is_ajax()` bằng kiểm tra header `X-Requested-With` (Django 3.1+)

**utils.py:**
- ✅ Thay thế `force_text` bằng `force_str` (Django 4.0+)

#### 2. Cập nhật Dependencies

**requirements.txt:**
- ✅ Django: `Django` → `Django>=3.2,<6.0`
- ✅ Markdown: `Markdown` → `Markdown>=3.0`
- ✅ Requests: `requests` → `requests>=2.20.0`

#### 3. Cập nhật Metadata

**setup.py:**
- ✅ Thêm hỗ trợ Django 3.2, 4.0, 4.1, 4.2, 5.0, 5.1
- ✅ Thêm hỗ trợ Python 3.8, 3.9, 3.10, 3.11, 3.12
- ✅ Loại bỏ các phiên bản Django và Python cũ không còn được hỗ trợ

**__init__.py:**
- ✅ Cập nhật version từ `1.4.9` → `1.5.0`

### Chi tiết thay đổi

#### views.py
```python
# Trước:
from django.utils.translation import ugettext_lazy as _

# Sau:
from django.utils.translation import gettext_lazy as _
```

```python
# Trước:
if request.method == 'POST' and request.is_ajax():

# Sau:
is_ajax = request.headers.get('X-Requested-With') == 'XMLHttpRequest'
if request.method == 'POST' and is_ajax:
```

#### utils.py
```python
# Trước:
from django.utils.encoding import force_text
return force_text(obj)

# Sau:
from django.utils.encoding import force_str
return force_str(obj)
```

### Tương thích

- ✅ Django 3.2 LTS
- ✅ Django 4.0, 4.1, 4.2 LTS
- ✅ Django 5.0, 5.1
- ✅ Python 3.8, 3.9, 3.10, 3.11, 3.12

### Kiểm tra

Tất cả các file đã được kiểm tra:
- ✅ views.py - Đã cập nhật
- ✅ utils.py - Đã cập nhật
- ✅ widgets.py - Không cần thay đổi
- ✅ fields.py - Không cần thay đổi
- ✅ models.py - Không cần thay đổi
- ✅ admin.py - Không cần thay đổi
- ✅ urls.py - Không cần thay đổi (đã hỗ trợ Django 2.0+)
- ✅ templatetags/martortags.py - Không cần thay đổi
- ✅ extensions/*.py - Không cần thay đổi
- ✅ tests/*.py - Không cần thay đổi

### Ghi chú

Các thay đổi này đảm bảo martor hoạt động tốt với Django 5.1 được sử dụng trong qhhoj-online-judge.
Tất cả các API đã bị loại bỏ đã được thay thế bằng các API mới tương thích.

