# djangoチュートリアル #13

## 管理サイトをカスタマイズしよう！中編 〜モデル一覧設定編〜

djangoの大きな特徴の１つは自動生成された管理サイトがついてくることです。  
今回はモデル一覧画面をカスタマイズします。

## 完成版プロジェクト

<https://github.com/shun-rec/django-website-13>

## 事前準備

### 新規サーバーを立ち上げる
[Paiza](https://paiza.cloud)で作業している方はdjangoにチェックを入れて新規サーバーを立ち上げて下さい。  
自分のマシンで作業している方はdjangoが使える作業用フォルダを作成して下さい。

### 前回管理サイトをカスタマイズしたプロジェクトをダウンロード

ターミナルを開いて、以下を実行。

```sh
git clone https://github.com/shun-rec/django-website-12
```

フォルダを移動

```sh
cd django-website-07
```

### マイグレートしてDBを作成

```sh
python manage.py migrate
```

### スーパーユーザーを作成

```sh
python manage.py createsuperuser
```

* ユーザー名: admin
* メールアドレス: （無し）
* パスワード: admin

## フィールドを変更しよう

verbose_name

## フィールドにユーザーのヘルプとなる注釈を表示しよう

help_text

## 表示するフィールドを制御しよう

fields

## 編集不可フィールドを表示しよう

readonly_fields

## フォームのフィールドを分類しよう

fieldsets

## フォームのさらなるカスタマイズ

```py
from django import forms

class CustomAdminForm(forms.ModelForm):
    class Meta:
        labels = {
            'title': 'ブログタイトル',
        }
```

ウォジェットの変え方は第７回、８回を参照して下さい。

## バリデーションの追加

普通はモデルに追加するのが良いことが多い。  
それが出来ない場合はFormに追加する。

```py
    def clean(self):
        body = self.cleaned_data.get('body')
        if '<' in body:
            raise forms.ValidationError('HTMLタグは使えません。')
```

## 保存時に処理を追加



```

```

## 関連モデルも同時に修正 - インライン

## 多対多フィールドを選択しやすっくしよう

filter_horizontal

## 新規作成フォームと編集フォームのテンプレートの上書き

change_form.html

admin直下に置けば全モデル。
admin/<アプリ名>下に置けば特定のアプリのみ
admin/<アプリ名>/<モデル名>/下に置けば特定のモデルのみ

## JSの読み込み

```js
(function($) {
  $(document).ready(function() {
    alert("JSが読み込まれました。")
  }
})(django.jQuery || jQuery);
```

