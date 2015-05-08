# webtraning
ポート番号

httpでは、80番。httpsでは、443番。

ネットワークのデータ通信を行うための道のようなもの。


ping

送信先と宛先とでIP通信できているか確認することができる

localhostの確認

inatomi-kento-no-macbook:Documents furyukyoutsuu$ ping localhost

PING localhost (127.0.0.1): 56 data bytes

64 bytes from 127.0.0.1: icmp_seq=0 ttl=64 time=0.063 ms

64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.100 ms

64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.098 ms


Github.comの確認

inatomi-kento-no-macbook:Documents furyukyoutsuu$ ping github.com

PING github.com (192.30.252.131): 56 data bytes

64 bytes from 192.30.252.131: icmp_seq=0 ttl=50 time=184.919 ms

64 bytes from 192.30.252.131: icmp_seq=1 ttl=50 time=194.916 ms

64 bytes from 192.30.252.131: icmp_seq=2 ttl=50 time=188.221 ms


サーバへの距離の違いによる通信時間やTTLに差があることが、はっきりとわかった。


traceroute

pingに似たもので、ネットワーク経路をリストとして表示する。


Github.comの確認

inatomi-kento-no-macbook:Documents furyukyoutsuu$ traceroute github.com

traceroute to github.com (192.30.252.129), 64 hops max, 52 byte packets

1  setup.netvolante.jp (192.168.1.1)  1.424 ms  0.842 ms  0.887 ms

2  163.139.100.121 (163.139.100.121)  2.690 ms  3.040 ms  2.709 ms

3  163.139.154.253 (163.139.154.253)  2.421 ms  2.769 ms  5.227 ms

4  163.139.154.217 (163.139.154.217)  6.615 ms  5.705 ms  4.329 ms

5  ae0.core2.doujima.vectant.ne.jp (163.139.129.74)  5.085 ms  5.030 ms  7.450 ms

6  ae-9.a20.osakjp01.jp.ra.gin.ntt.net (61.200.82.117)  14.053 ms  15.934 ms  12.211 ms


どこを通過しているかわかり、また、複数の場所を通過していることがわかる。


ファイアウォール

パケットフィルタリング型

クライアント側がファイアウォールを通してサーバにアクセスする際に、

アドレスを書き換えないで通信をする。

また、NATを使用してアドレスを書き換えることで、通信相手のサーバから

クライアントの存在を隠すことができる。


プロキシ型

クライアントからの要求を代理でファイアウォールがサーバにアクセスする、

つまり、クライアントの存在をサーバから隠すことができる。

パケットフィルタリング型とは違い、アクセス制限などの細かい設定が可能である。


課題

1.IPアドレスを変更、または存在しないIPを指定

→hostが見つからないため、”ページを開けません”エラーが出る

2.ポート番号を変更させる

→apacheのポート番号の設定が違うため、”サーバに接続できません”エラーが出る

3.Webサーバを停止させる

→sudo apachectl stopで停止させる、”サーバに接続できません”エラーが出る

4.存在しないHTMLファイルを指定する

”Not Found”エラーが出る

5.ケーブルを抜く。スイッチの電源を切る

”ページを開けません”エラーが出る


これらのことから、エラーに違いがあることがわかった。

原因を特定するときのポイントとなると考えられる。