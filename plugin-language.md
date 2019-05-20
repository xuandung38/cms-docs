# Language

## Apply multi language for your new plugin

- Open `/plugins/<your-plugin>/src/Providers/<YourPlugin>ServiceProvider.php`. Add below code to function `boot`

```php
if (defined('LANGUAGE_MODULE_SCREEN_NAME')) {
    \Language::registerModule([<YOUR_PLUGIN>_MODULE_SCREEN_NAME]);
}
```
## Language switcher

### Adding language switcher to your theme.

Add to your theme views.

```
{!! apply_filters('language_switcher') !!}
```

### Customize swicher.

If you want to custom language swicher, you can use this html instead of using `apply_filters`. It's located in `platform/plugins/language/resources/views/partials/switcher.blade.php`

```
@if ($supported_locales)
    @php
        $language_display = setting('language_display', 'all');
        $show_related = setting('language_show_default_item_if_current_version_not_existed', true);
    @endphp
    @if (setting('language_switcher_display', 'dropdown') == 'dropdown')
        {!! Arr::get($options, 'before') !!}
        <div class="dropdown">
            <button class="btn btn-secondary dropdown-toggle" type="button" data-toggle="dropdown" aria-haspopup="true" aria-expanded="true">
                @if (Arr::get($options, 'lang_flag', true) && ($language_display == 'all' || $language_display == 'flag'))
                    {!! language_flag(Language::getCurrentLocaleFlag(), Language::getCurrentLocaleName()) !!}
                @endif
                @if (Arr::get($options, 'lang_name', true) && ($language_display == 'all' || $language_display == 'name'))
                    {{ Language::getCurrentLocaleName() }}
                @endif
                <span class="caret"></span>
            </button>
            <ul class="dropdown-menu language_bar_chooser {{ Arr::get($options, 'class') }}">
                @foreach ($supported_locales as $localeCode => $properties)
                    <li @if ($localeCode == Language::getCurrentLocale()) class="active" @endif>
                        <a rel="alternate" hreflang="{{ $localeCode }}" href="{{ $show_related ? Language::getLocalizedURL($localeCode) : url($localeCode) }}">
                            @if (Arr::get($options, 'lang_flag', true) && ($language_display == 'all' || $language_display == 'flag')){!! language_flag($properties['lang_flag'], $properties['lang_name']) !!}@endif
                            @if (Arr::get($options, 'lang_name', true) && ($language_display == 'all' || $language_display == 'name'))<span>{{ $properties['lang_name'] }}</span>@endif
                        </a>
                    </li>
                @endforeach
            </ul>
        </div>
        {!! Arr::get($options, 'after') !!}
    @else
        <ul class="language_bar_list {{ Arr::get($options, 'class') }}">
            @foreach ($supported_locales as $localeCode => $properties)
                <li @if ($localeCode == Language::getCurrentLocale()) class="active" @endif>
                    <a rel="alternate" hreflang="{{ $localeCode }}" href="{{ $show_related ? Language::getLocalizedURL($localeCode) : url($localeCode) }}">
                        @if (Arr::get($options, 'lang_flag', true) && ($language_display == 'all' || $language_display == 'flag')){!! language_flag($properties['lang_flag'], $properties['lang_name']) !!}@endif
                        @if (Arr::get($options, 'lang_name', true) && ($language_display == 'all' || $language_display == 'name'))<span>{{ $properties['lang_name'] }}</span>@endif
                    </a>
                </li>
            @endforeach
        </ul>
    @endif
@endif
```
