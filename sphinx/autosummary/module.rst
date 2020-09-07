{{ objname }} *(module)*
{{ underline }}===========



.. automodule:: {{ fullname }}
    :members:
    :undoc-members:
    :show-inheritance:
    :inherited-members:
    :member-order: groupwise
    
    {% block classes %}
    {% if classes %}
    .. rubric:: Classes

    .. autosummary::
    {% for item in classes %}
      ~{{ item }}
    {%- endfor %}
    {% endif %}
    {% endblock %}

    {% block functions %}
    {% if functions %}
    .. rubric:: Functions

    .. autosummary::
    {% for item in functions %}
      ~{{ item }}
    {%- endfor %}
    {% endif %}
    {% endblock %}

    {% block attributes %}
    {% if attributes %}
    .. rubric:: Properties

    .. autosummary::
    {% for item in attributes %}
      ~{{ item }}
    {%- endfor %}
    {% endif %}
    {% endblock %}

    {% block members %}
    {% if members %}
    {% set printMe = [] %}
    
    {% for item in members %}
    {% if "__" not in item and "_" not in item|first and "absolute_import" not in item  %}
        {% if "test" not in item %}
            {% if printMe.append(1) %}{% endif %}
            {{ printMe }}
       {% endif %}
    {% endif %}
    {%- endfor %}
    {% endif %}

    {% if printMe|length > 0 %}
    .. rubric:: Sub-modules

    .. autosummary::
    {% for item in members %}
    {% if "__" not in item and "_" not in item|first and "absolute_import" not in item  %}
        {% if "test" not in item %}
            ~{{ item }}
       {% endif %}
    {% endif %}
    {%- endfor %}

    {% for item in members %}
            ~{{ item }}

    {%- endfor %}


    {% endif %}

    
    {% endblock %}
