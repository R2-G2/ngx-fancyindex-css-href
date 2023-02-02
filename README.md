<!-- Copyright (c) 2022 Ralf Grawunder -->

# ngx-fancyindex-css-href: override the default CSS

## Usage

Tell the [**Nginx Fancy Index module**](https://github.com/aperezdc/ngx-fancyindex) to load an aliased CSS file with
*SSI* enabled.

```nginx
location / {
    fancyindex on;
    fancyindex_css_href /fancyindex.css;

    location = /fancyindex.css {
        # git clone https://gist.github.com/452522be0ef3813c45a5dee5b11ef539.git /opt/ngx-fancyindex-css-href
        alias /opt/ngx-fancyindex-css-href/fancyindex.css;
        ssi on;
        ssi_types text/css;
    }
}
```

You can also define you own (e.g. dark) colors.

```nginx
location /DIRECTORY/ {
    fancyindex on;
    fancyindex_css_href /DIRECTORY/DARK.css;

    location = /DIRECTORY/DARK.css {
        # git clone https://gist.github.com/452522be0ef3813c45a5dee5b11ef539.git /CUSTOM/PATH
        alias /CUSTOM/PATH/fancyindex.css;
        ssi on;
        ssi_types text/css;
        set $ficss_color_background_normal "#000";
        set $ficss_color_background_highlight "#111";
        set $ficss_color_border "#222";
        set $ficss_color_text "#777";
        set $ficss_color_link "#bbb";
        set $ficss_color_hover "#fff";
    }
}
```

## Problems?

Fork! Fork it! Fork you! Fork me, right?
