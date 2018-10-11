FROM wordpress:latest

# 必要なツールをインストール
RUN apt-get update
RUN apt-get -y install unzip

# WP プラグイン (zip) ダウンロード
WORKDIR /tmp/wp-plugins
RUN curl -O https://downloads.wordpress.org/plugin/wp-multibyte-patch.2.8.1.zip

# Zip ファイルを解凍してインストール
RUN unzip './*.zip' -d /usr/src/wordpress/wp-content/plugins

# 不要になった一時ファイルを削除
RUN apt-get clean
RUN rm -rf /tmp/*

# サーバが読めるように wp-content 以下の所有者を変更
RUN chown -R www-data:www-data /usr/src/wordpress/wp-content

# MailHog でメールを受信できるように設定
RUN curl --location --output /usr/local/bin/mhsendmail https://github.com/mailhog/mhsendmail/releases/download/v0.2.0/mhsendmail_linux_amd64
RUN chmod +x /usr/local/bin/mhsendmail
RUN echo 'sendmail_path="/usr/local/bin/mhsendmail --smtp-addr=mailhog:1025 --from=no-reply@docker.dev"' > /usr/local/etc/php/conf.d/mailhog.ini

WORKDIR /var/www/html