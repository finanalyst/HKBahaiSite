# Critical Files for the GRAV site at hk.bahai.org

Only those files that differ from a standard GRAV installation with the Quark theme.

BUT ... the shortcode plugin for `[size]` currently does not support attributes like 'xx-large'.

So the following needs to be the contents of `user/plugins/shortcode-core/shortcodes/SizeShortcode.php`
```
<?php
namespace Grav\Plugin\Shortcodes;

use Thunder\Shortcode\Shortcode\ShortcodeInterface;

class SizeShortcode extends Shortcode
{
    public function init()
    {
        $this->shortcode->getHandlers()->add('size', function(ShortcodeInterface $sc) {
            $size = $sc->getParameter('size', $sc->getBbCode());
            if ( is_numeric($size) ) { $size = $size.'px' ; }
            return '<span style="font-size: '.$size.';">'.$sc->getContent().'</span>';
        });
    }
}
```
