## Django Admin View Change Attribues

---

Here are some common attributes that can be used in the Django Admin interface:

> list_display: A tuple of field names that are displayed in the list view of the admin site. For example, 

```python
    list_display = ('title', 'author', 'pub_date').
```

> list_filter: A tuple of field names that are used to filter the list view by certain criteria. For example, 

```python
    list_filter = ('author', 'pub_date').
```
> search_fields: A tuple of field names that are used to search for specific records in the list view. For example, 

```python
    search_fields = ('title', 'author__name').
```

> list_editable: A tuple of field names that can be edited directly in the list view. For example, 

```python
    list_editable = ('status',).
```
> list_per_page: The number of records displayed per page in the list view. For example, 

```python
    list_per_page = 25.
```

> ordering: A tuple of field names used to specify the default order of records in the list view. For example, 

```python
    ordering = ('-pub_date',).
```

> date_hierarchy: A string representing the name of the date field that is used to provide a hierarchical date-based navigation in the admin site. For example, 

 ```python 
    date_hierarchy = 'pub_date'.
```
> actions: A list of functions that can be performed on selected records in the admin site. For example:

```python
def make_published(modeladmin, request, queryset):
    queryset.update(status='published')
make_published.short_description = "Mark selected articles as published"

class ArticleAdmin(admin.ModelAdmin):
    actions = [make_published]

```
> actions_on_bottom: A boolean value that specifies whether the action buttons should be displayed at the bottom of the admin site. For example:

```python
class ArticleAdmin(admin.ModelAdmin):
    actions_on_bottom = True
```

> actions_on_top: A boolean value that specifies whether the action buttons should be displayed at the top of the admin site. For example:

```python 
class ArticleAdmin(admin.ModelAdmin):
    actions_on_top = True

```

> actions_selection_counter: A boolean value that specifies whether the number of selected records should be displayed next to the action buttons. For example:

```python
class ArticleAdmin(admin.ModelAdmin):
    actions_selection_counter = True

```

> autocomplete_fields: A tuple of foreign key fields that allow you to quickly select related records in the admin site. For example:

```python
class ArticleAdmin(admin.ModelAdmin):
    autocomplete_fields = ['author', 'tags']

```

> empty_value_display: A string that is displayed for fields with a null or empty value. For example:

```python
class ArticleAdmin(admin.ModelAdmin):
    empty_value_display = '-empty-'

```
> exclude: A list of fields that should be excluded from the admin site. For example:

```python 
class ArticleAdmin(admin.ModelAdmin):
    exclude = ['slug']

```

> fields: A tuple of fields that should be displayed in the detail view of the admin site. For example:

```python
class ArticleAdmin(admin.ModelAdmin):
    fields = ('title', 'author', 'body')

```

> fieldsets: A list of fieldsets that should be displayed in the detail view of the admin site. For example:

```python
class ArticleAdmin(admin.ModelAdmin):
    fieldsets = (
        ('Metadata', {
            'fields': ('title', 'author', 'pub_date')
        }),
        ('Content', {
            'fields': ('body', 'tags')
        })
    )

```

> filter_horizontal: A tuple of many-to-many fields that are displayed in a horizontal widget in the admin site. For example:

```python
class ArticleAdmin(admin.ModelAdmin):
    filter_horizontal = ['tags']

```

> filter_vertical: A tuple of many-to-many fields that are displayed in a vertical widget in the admin site. For example:

```python
class ArticleAdmin(admin.ModelAdmin):
    filter_vertical = ['tags']
```
> form: A custom form that is used to validate and process data in the admin site. For example:

```python
from django import forms

class ArticleAdminForm(forms.ModelForm):
    class Meta:
        model = Article
        fields = '__all__'
        widgets = {
            'body': forms.Textarea(attrs={'rows': 10}),
        }

class ArticleAdmin(admin.ModelAdmin):
    form = ArticleAdminForm

```




These attributes can be defined in the admin.py file of the Django application. By using these attributes, you can customize the look and feel of the Django Admin interface to suit your specific needs.





