pkgname=gitlab-gollum
pkgver=1
pkgrel=1
pkgdesc="Embeds the gollum wiki in gitlab"
arch=('i686' 'x86_64')
depends=('gitlab>=7.0.0')
source=(
    "git+file://$HOME/programming/ruby/dev/projects/gitlab_gollum/gitlab_gollum"
    gitlab-gollum.service
)
md5sums=(
    'SKIP'
    'SKIP'
)

_srcdir="gitlab_gollum"

build(){
    cd "${srcdir}/${_srcdir}"
    bundle config build.nokogiri --use-system-libraries
    bundle install --no-cache --path vendor/bundle
}

package(){
    mkdir -p "${pkgdir}/usr/share/webapps"
    cp -r "${srcdir}/${_srcdir}" "${pkgdir}/usr/share/webapps/gitlab-gollum"
    chown -R gitlab:gitlab "${pkgdir}/usr/share/webapps/gitlab-gollum"
    mkdir -p "${pkgdir}/usr/lib/systemd/system/"
    cp "${srcdir}/gitlab-gollum.service" "${pkgdir}/usr/lib/systemd/system/"
}
