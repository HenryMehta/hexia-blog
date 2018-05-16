=====
Blog
=====

Blog is a simple Django Blog app.  

Blogs can have tags,  title, image, short description and a rich text blog.

Tags are created in Admin and Users can then add as many as they like.

Detailed documentation is needs writing.

Quick start
-----------

1. pip install hexia-blog

2. Add "blog" and dependencies to your INSTALLED_APPS setting like this::

    INSTALLED_APPS = [
        ...
        'ckeditor',
        'ckeditor_uploader',
        'blog',
    ]

3. Add "blog.context_processors.hexia_blog" to your context_processors
        'OPTIONS': {
            'context_processors': [
                ...
                'blog.context_processors.hexia_blog',
            ],
        },


4. Include the polls URLconf in your project urls.py like this::

    path('blog/', include('blog.urls')),

5. Run `python manage.py migrate` to create the polls models.

6. Start the development server and visit http://127.0.0.1:8000/admin/
   to create a Category (you'll need the Admin app enabled).

7. There are 3 URLs provide.
   <a href="{% url 'blog:blog-detail' object.slug %}">Blog Detail</a> will provide the detail of a specific blog.
   Template: blog/blog_detail.html

   <a href="{% url 'blog:blog-list' %}">Blog List</a> will list all blogs.
   Template: blog/blog_list.html
   There is a special case of list where 'tag' and/or 'search_string' get be set.  When set, only blogs matching 
   these criteria will be returned.  See blog/blog_list.html to see it implemented.

   <a href="{% url 'blog:blog-create' %}">Blog Create</a> will allow you to create a new blog (or you can via admin)
   Template: blog/blog_form.html
   When using this you must set the blog auther to the user who it is associated with.
   
8. Visit http://127.0.0.1:8000/.


Settings
--------

Blog uses AUTH_USER_MODEL as the default user model.  It will default to
the Django User model if AUTH_USER_MODEL is not set in settings.py

BLOG_PAGINATION:
The number of blogs shown on a single page when using listing.
Default = 20

Context Processors
------------------
There is a single context_processor provided, 'hexia_blog_tags', which provides a list of all Tags.
It is used in blog_list.html.