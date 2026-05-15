Hlavní zranitelností systému byla chybně nastavená práva k adresáři /usr/bin (drwxr-xrwx), která umožnila libovolnému uživateli mazat a vytvářet soubory v systémové cestě.
SUID binárka /usr/local/bin/sysreport (vlastněná uživatelem spravce) volala pevnou cestu k utilitě /usr/bin/id.
Nahrazením této utility vlastním skriptem došlo k přenosu efektivních práv (EUID 1001) na útočníkův kód. Použití přepínače -p v shellu zajistilo zachování těchto privilegií i během vykonávání skriptu.
Díky této eskalaci bylo možné přečíst soubor /home/spravce/.flag, ke kterému má běžný uživatel student přístup odepřen.
