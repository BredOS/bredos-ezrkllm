# Maintainer: Bill Sideris <bill88t@bredos.org>

pkgname=ezrknn-llm
pkgver=r147.29fbc9b
pkgrel=1
arch=('aarch64')
pkgdesc="RKNN LLM demo"
url="https://github.com/Pelochus/ezrknn-llm/"
license=('custom')
depends=('gcc' 'cmake' 'make' 'rkllm_api')
source=(git+https://github.com/Pelochus/"$pkgname" "CMakeLists.txt")
sha256sums=('SKIP' 'SKIP')

pkgver() {
    cd "$srcdir/$pkgname"
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
    cd "$srcdir/$pkgname/rkllm-runtime/examples/rkllm_api_demo/"
    cp "$srcdir/CMakeLists.txt" "$srcdir/$pkgname/rkllm-runtime/examples/rkllm_api_demo/"

    mkdir build && cd build

    cmake .. \
        -DCMAKE_SYSTEM_PROCESSOR="aarch64" \
        -DCMAKE_SYSTEM_NAME=Linux \
        -DCMAKE_C_COMPILER=/usr/bin/gcc \
        -DCMAKE_CXX_COMPILER=/usr/bin/g++ \
        -DCMAKE_BUILD_TYPE=/usr/bin/strip \
        -DCMAKE_POSITION_INDEPENDENT_CODE=ON

    make -j$(nproc)
}

package() {
    cd "$srcdir/$pkgname"
    mkdir -p "$pkgdir/usr/bin"
    install -Dm755 rkllm-runtime/examples/rkllm_api_demo/build/llm_demo "$pkgdir/usr/bin/rkllm"
}
