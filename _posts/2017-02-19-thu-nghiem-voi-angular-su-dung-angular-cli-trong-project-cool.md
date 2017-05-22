---
id: 293
title: 'Thử Nghiệm Với Angular Phần 10: Sử Dụng Angular CLI Trong Project Thật Cool'
date: 2017-02-19T10:36:03+00:00
author: Tiep Phan
layout: post
guid: http://www.tiepphan.com/?p=293
permalink: /thu-nghiem-voi-angular-su-dung-angular-cli-trong-project-cool/
beans_layout:
  - default_fallback
image: /wp-content/uploads/2017/02/angular2-10.jpg
categories:
  - Lập Trình
  - Lập Trình Angular
  - Programming
  - Web
tags:
  - Angular
  - Angular 2
  - Angular CLI
  - Lập Trình Angular 2
---
<h2 style="text-align: center;">
  Sử Dụng Angular CLI Trong Project Thật Cool
</h2>

Trong <a href="http://www.tiepphan.com/thu-nghiem-voi-angular-2-component-va-data-binding/" target="_blank">bài học đầu tiên</a> của series Thử Nghiệm Với Angular, chúng ta đã tạo project để thực hành với sự trợ giúp của Angular CLI. Trong bài này, chúng ta sẽ tìm hiểu cách sử dụng CLI để phát triển một ứng dụng bằng Angular và build một ứng dụng Angular với Angular CLI.

<!--more-->

### 1. Các phần mềm cần thiết:

Để bắt đầu cài đặt được Angular CLI &#8211; gọi tắt là CLI &#8211; gồm có

  * <a href="https://nodejs.org/en/" target="_blank">Nodejs</a>
  * <a href="https://www.typescriptlang.org/" target="_blank">TypeScript</a>
  * <a href="https://yarnpkg.com/en/docs/install" target="_blank">Yarn Package Manager</a>

### 2. Cài đặt CLI:

<pre class="brush:shell;">npm install -g @angular/cli
// or
npm i -g @angular/cli
// or sudo if need
sudo npm install -g @angular/cli
// or
sudo npm i -g @angular/cli</pre>

### 3. Sử dụng CLI:

&#8211; List các options của CLI:

<pre class="brush:shell;">ng help</pre>

&#8211; Tạo mới project với CLI:

<pre class="brush:shell;">ng new &lt;app-name&gt;
// example
ng new contact-app
// use preprocessor instead of css: scss, sass, stylus, less
ng new contact-app --style=scss
</pre>

Các options khác:

<pre class="brush:shell;">--ng4: tạo ứng dụng Angular với Angular v4
--routing: tạo route
--skip-git: không init và commit git
--skip-install: không install package
--skip-commit: init git nhưng không commit
--source-dir: thư mục của source code, mặc định là src
--prefix: prefix khi generate component, directive, mặc đinh là app
--inline-style: sử dụng inline style thay vì external style file
--inline-template: sử dụng inline template thay vì external template file
-is: alias của --inline-style
-it: alias của --inline-template
-si: alias của --skip-install
-sg: alias của --skip-git
</pre>

&#8211; Generate các thành phần:

| Scaffold  | Usage                             |
| --------- | --------------------------------- |
| Component | `ng g component my-new-component` |
| Directive | `ng g directive my-new-directive` |
| Pipe      | `ng g pipe my-new-pipe`           |
| Service   | `ng g service my-new-service`     |
| Class     | `ng g class my-new-class`         |
| Interface | `ng g interface my-new-interface` |
| Enum      | `ng g enum my-new-enum`           |
| Module    | `ng g module my-module`           |

&#8211; Serve ứng dụng:

<pre class="brush:shell;">ng serve &lt;options...&gt;
  Builds and serves your app, rebuilding on file changes.
  aliases: server, s
  --target (String) (Default: development)
    aliases: -t &lt;value&gt;, -dev (--target=development), -prod (--target=production), --target &lt;value&gt;, --target &lt;value&gt;, --target &lt;value&gt;, --target &lt;value&gt;
  --environment (String)
    aliases: -e &lt;value&gt;, --environment &lt;value&gt;, --environment &lt;value&gt;, --environment &lt;value&gt;, --environment &lt;value&gt;
  --output-path (Path)
    aliases: -op &lt;value&gt;, --outputPath &lt;value&gt;, --outputPath &lt;value&gt;, --outputPath &lt;value&gt;, --outputPath &lt;value&gt;
  --aot (Boolean)
    aliases: -aot, -aot, -aot, -aot
  --sourcemap (Boolean)
    aliases: -sm, --sourcemaps, --sourcemap, --sourcemap, --sourcemap, --sourcemap
  --vendor-chunk (Boolean) (Default: true)
    aliases: -vc, --vendorChunk, --vendorChunk, --vendorChunk, --vendorChunk
  --base-href (String)
    aliases: -bh &lt;value&gt;, --baseHref &lt;value&gt;, --baseHref &lt;value&gt;, --baseHref &lt;value&gt;, --baseHref &lt;value&gt;
  --deploy-url (String)
    aliases: -d &lt;value&gt;, --deployUrl &lt;value&gt;, --deployUrl &lt;value&gt;, --deployUrl &lt;value&gt;, --deployUrl &lt;value&gt;
  --verbose (Boolean) (Default: false)
    aliases: -v, --verbose, --verbose, --verbose, --verbose
  --progress (Boolean) (Default: true)
    aliases: -pr, --progress, --progress, --progress, --progress
  --i18n-file (String)
    aliases: --i18nFile &lt;value&gt;, --i18nFile &lt;value&gt;, --i18nFile &lt;value&gt;, --i18nFile &lt;value&gt;
  --i18n-format (String)
    aliases: --i18nFormat &lt;value&gt;, --i18nFormat &lt;value&gt;, --i18nFormat &lt;value&gt;, --i18nFormat &lt;value&gt;
  --locale (String)
    aliases: --locale &lt;value&gt;, --locale &lt;value&gt;, --locale &lt;value&gt;, --locale &lt;value&gt;
  --extract-css (Boolean)
    aliases: -ec, --extractCss, --extractCss, --extractCss, --extractCss
  --watch (Boolean)
    aliases: -w, --watch, --watch, --watch, --watch
  --output-hashing=none|all|media|bundles (String) define the output filename cache-busting hashing mode
    aliases: -oh &lt;value&gt;, --outputHashing &lt;value&gt;, --outputHashing &lt;value&gt;, --outputHashing &lt;value&gt;, --outputHashing &lt;value&gt;
  --poll (Number) enable and define the file watching poll time period (milliseconds)
    aliases: -poll &lt;value&gt;, -poll &lt;value&gt;, -poll &lt;value&gt;, -poll &lt;value&gt;
  --port (Number) (Default: 4200)
    aliases: -p &lt;value&gt;, -port &lt;value&gt;, -port &lt;value&gt;
  --host (String) (Default: localhost) Listens only on localhost by default
    aliases: -H &lt;value&gt;, -host &lt;value&gt;, -host &lt;value&gt;
  --proxy-config (Path)
    aliases: -pc &lt;value&gt;, --proxyConfig &lt;value&gt;, --proxyConfig &lt;value&gt;
  --ssl (Boolean) (Default: false)
    aliases: -ssl, -ssl
  --ssl-key (String) (Default: ssl/server.key)
    aliases: --sslKey &lt;value&gt;, --sslKey &lt;value&gt;
  --ssl-cert (String) (Default: ssl/server.crt)
    aliases: --sslCert &lt;value&gt;, --sslCert &lt;value&gt;
  --open (Boolean) (Default: false) Opens the url in default browser
    aliases: -o, -open, -open
  --live-reload (Boolean) (Default: true)
    aliases: -lr, --liveReload
  --live-reload-host (String) Defaults to host
    aliases: -lrh &lt;value&gt;, --liveReloadHost &lt;value&gt;
  --live-reload-base-url (String) Defaults to baseURL
    aliases: -lrbu &lt;value&gt;, --liveReloadBaseUrl &lt;value&gt;
  --live-reload-port (Number) (Defaults to port number within [49152...65535])
    aliases: -lrp &lt;value&gt;, --liveReloadPort &lt;value&gt;
  --live-reload-live-css (Boolean) (Default: true) Whether to live reload CSS (default true)
    aliases: --liveReloadLiveCss
  --hmr (Boolean) (Default: false) Enable hot module replacement
    aliases: -hmr
</pre>

&nbsp;

&#8211; Build ứng dụng:

<pre class="brush:shell;">ng build &lt;options...&gt;

options có thể có hoặc không.

--aot=true: build với AOT
--aot=false: không build với AOT.

# build production
--target=production --environment=prod
--prod --env=prod
--prod
# build dev: default
--target=development --environment=dev
--dev --e=dev
--dev

Complete options available
Builds your app and places it into the output path (dist/ by default).
  aliases: b
  --target (String) (Default: development)
    aliases: -t &lt;value&gt;, -dev (--target=development), -prod (--target=production), --target &lt;value&gt;
  --environment (String)
    aliases: -e &lt;value&gt;, --environment &lt;value&gt;
  --output-path (Path)
    aliases: -op &lt;value&gt;, --outputPath &lt;value&gt;
  --aot (Boolean)
    aliases: -aot
  --sourcemap (Boolean)
    aliases: -sm, --sourcemaps, --sourcemap
  --vendor-chunk (Boolean) (Default: true)
    aliases: -vc, --vendorChunk
  --base-href (String)
    aliases: -bh &lt;value&gt;, --baseHref &lt;value&gt;
  --deploy-url (String)
    aliases: -d &lt;value&gt;, --deployUrl &lt;value&gt;
  --verbose (Boolean) (Default: false)
    aliases: -v, --verbose
  --progress (Boolean) (Default: true)
    aliases: -pr, --progress
  --i18n-file (String)
    aliases: --i18nFile &lt;value&gt;
  --i18n-format (String)
    aliases: --i18nFormat &lt;value&gt;
  --locale (String)
    aliases: --locale &lt;value&gt;
  --extract-css (Boolean)
    aliases: -ec, --extractCss
  --watch (Boolean)
    aliases: -w, --watch
  --output-hashing=none|all|media|bundles (String) define the output filename cache-busting hashing mode
    aliases: -oh &lt;value&gt;, --outputHashing &lt;value&gt;
  --poll (Number) enable and define the file watching poll time period (milliseconds)
    aliases: -poll &lt;value&gt;
  --stats-json (Boolean) (Default: false)
    aliases: --statsJson
</pre>

### 4. Video bài học:



Ahead-of-time compilation: <a href="https://angular.io/docs/ts/latest/cookbook/aot-compiler.html" target="_blank">https://angular.io/docs/ts/latest/cookbook/aot-compiler.html</a>