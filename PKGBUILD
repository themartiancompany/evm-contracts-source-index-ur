# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2023, 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Contributor: Fabio Castelli (muflone) <webreg@muflone.com>

_proj="hip"
_Proj="humaninstrumentalityproject.org"
_git="false"
_offline="false"
_hardhat="true"
_solc="true"
_pkg=ur
pkgbase="${_pkg}"
pkgname=(
  "${pkgbase}"
  "${pkgbase}-contracts"
)
_pkgdesc=(
  "Distributed, decentralized,"
  "uncensorable, cross-platform"
  "user repository and application store"
  "designed for Life and DogeOS."
)
pkgdesc="${_pkgdesc[*]}"
url="https://www.${_Proj}.org"
pkgver="0.1.1.1"
_commit="c2615421b463a3a6a90db9def09267b9d20a41bc"
pkgrel=1
arch=(
  'any'
)
license=(
  'AGPL3'
)
_tarname="${_pkg}-${pkgver}"
_arch_ns="tallero"
_gh_ns="themartiancompany"
_arch="gitlab.archlinux.org"
_gh="github.com"
_host="${_gh}"
_ns="${_gh_ns}"
_ssh="ssh://git@${_host}:${_ns}/${_pkg}"
_local="file://${HOME}/${_pkg}"
_http="https://${_host}/${_ns}/${_pkg}"
_url="${_http}"
depends=(
  "evm-gnupg"
  "fur"
  "libcrash-bash"
  "lur"
)
makedepends=(
  'evm-make'
  'make'
)
if [[ "${_solc}" == "true" ]]; then
  makedepends+=(
    "solidity=0.8.28"
  )
fi
if [[ "${_hardhat}" == "true" ]]; then
  makedepends+=(
    "hardhat"
  )
fi
checkdepends=(
  'shellcheck')
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${pkgname}"
fi
if [[ "${_git}" == true ]]; then
  makedepends+=(
    "git"
  )
  _src="${_tarname}::git+${_url}#${_tag_name}=${_tag}?signed"
  _sum="SKIP"
elif [[ "${_git}" == false ]]; then
  if [[ "${_tag_name}" == 'pkgver' ]]; then
    _src="${_tarname}.tar.gz::${_url}/archive/refs/tags/${_tag}.tar.gz"
    _sum="d4f4179c6e4ce1702c5fe6af132669e8ec4d0378428f69518f2926b969663a91"
  elif [[ "${_tag_name}" == "commit" ]]; then
    _src="${_tarname}.zip::${_url}/archive/${_commit}.zip"
    _sum='076c50653af1a1330656c36db1e0b3e3a8fa53e06c801015d964f9515c24cec9'
  fi
fi
source=(
  "${_src}"
)
sha256sums=(
  "${_sum}"
)

check() {
  cd \
    "${pkgname}"
  make \
    -k \
    check
}

build() {
  local \
    _make_opts=()
  _make_opts=(
    --debug
  )
  cd \
    "${_tarname}"
  if [[ "${_solc}" == "true" ]]; then
    SOLIDITY_COMPILER_BACKEND="solc" \
    make \
      "${_make_opts[@]}" \
      all
  fi
  if [[ "${_hardhat}" == "true" ]]; then
    SOLIDITY_COMPILER_BACKEND="hardhat" \
    make \
      "${_make_opts[@]}" \
      all
  fi
}

package_ur-contracts() {
  local \
    _make_opts=()
  _make_opts=(
    DESTDIR="${pkgdir}"
    PREFIX='/usr'
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-contracts-sources
  make \
    "${_make_opts[@]}" \
    install-contracts-deployments-config
  if [[ "${_solc}" == "true" ]]; then
    make \
      "${_make_opts[@]}" \
      install-contracts-deployments-solc
  fi
  if [[ "${_hardhat}" == "true" ]]; then
    make \
      "${_make_opts[@]}" \
      install-contracts-deployments-hardhat
  fi
}

package_ur() {
  local \
    _make_opts=()
  _make_opts=(
    DESTDIR="${pkgdir}"
    PREFIX='/usr'
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-scripts
  make \
    "${_make_opts[@]}" \
    install-doc
}

