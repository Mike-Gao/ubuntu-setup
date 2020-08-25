# Mike's Ubuntu Setup Scripts

Preferring Chinese Fonts to Japanese Fonts

#### **`/etc/fonts/conf.d/64-language-selector-prefer.conf`**
```xml
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
	<alias>
		<family>sans-serif</family>
		<prefer>
			<family>Noto Sans CJK SC</family>
			<family>Noto Sans CJK TC</family>
			<family>Noto Sans CJK HK</family>
			<family>Noto Sans CJK JP</family>
			<family>Noto Sans CJK KR</family>
			<family>Lohit Devanagari</family>
		</prefer>
	</alias>
	<alias>
		<family>serif</family>
		<prefer>
			<family>Noto Serif CJK SC</family>
			<family>Noto Serif CJK TC</family>
			<family>Noto Serif CJK JP</family>
			<family>Noto Serif CJK KR</family>
			<family>Lohit Devanagari</family>
		</prefer>
	</alias>
	<alias>
		<family>monospace</family>
		<prefer>
			<family>Noto Sans Mono CJK SC</family>
			<family>Noto Sans Mono CJK TC</family>
			<family>Noto Sans Mono CJK HK</family>
			<family>Noto Sans Mono CJK JP</family>
			<family>Noto Sans Mono CJK KR</family>
		</prefer>
	</alias>
</fontconfig>
```
