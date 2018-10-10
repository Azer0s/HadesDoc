# Installing Hades

## Installing a via an install script

Installing is as easy as pasting a command in your command-line.

{% tabs %}
{% tab title="Windows" %}
## With chocolatey

```bash
choco install hadeslang
```

## Without chocolatey \(powershell\)

```bash
iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/Azer0s/HadesLang/master/install.ps1'))
```
{% endtab %}

{% tab title="Linux" %}
```bash
wget -O - https://raw.githubusercontent.com/Azer0s/HadesLang/master/install.sh | bash
```
{% endtab %}
{% endtabs %}

## Compiling yourself

On Linux and MacOS you can compile and install Hades manually.

### Prerequisites

* make
* dotnet-core
* git

### Installation process

```bash
git clone https://github.com/Azer0s/HadesLang.git
cd HadesLang
./configure # choose default libraries and install path
make
make install
```

