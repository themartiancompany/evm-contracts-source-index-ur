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

_os="$( \
  uname \
    -o)"
_evmfs_available="$( \
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
_py="python"
_proj="hip"
_Proj="humaninstrumentalityproject.org"
_git="false"
_contracts="true"
_docs="true"
_hardhat="true"
_solc="true"
_pkg=ur
pkgbase="${_pkg}"
pkgname=(
  "${pkgbase}"
)
if [[ "${_contracts}" == "true" ]]; then
  pkgname+=(
    "${_pkg}-contracts"
  )
fi
if [[ "${_docs}" == "true" ]]; then
  pkgname+=(
    "${_pkg}-docs"
  )
fi
_pkgdesc=(
  "Distributed, decentralized,"
  "uncensorable, cross-platform"
  "user repository and application store"
  "designed for Life and DogeOS."
)
pkgdesc="${_pkgdesc[*]}"
url="https://www.${_Proj}.org"
pkgver="0.1.1.1"
_commit="b5daa25e7f3d7641468e869e973b3cd3850fbba4"
pkgrel=1
arch=(
  'any'
)
license=(
  'AGPL3'
)
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
  "evm-contracts-tools"
  "evm-gnupg"
  "evm-wallet"
  "fur"
  "libcrash-bash"
  "libevm"
  "lur"
)
makedepends=(
  'make'
)
if [[ "${_docs}" == "true" ]]; then
  makedepends+=(
    "${_py}-docutils"
  )
fi
if [[ "${_contracts}" == "true" ]]; then
  makedepends+=(
    'evm-make'
  )
  if [[ "${_solc}" == "true" ]]; then
    makedepends+=(
      "solidity=0.8.28"
      "solidity=0.8.24"
    )
  fi
  if [[ "${_hardhat}" == "true" ]]; then
    makedepends+=(
      "hardhat"
    )
  fi
fi
checkdepends=(
  'shellcheck'
)
_pub_optdepends=(
  "pub:"
    "for publishing applications"
    "on the repository and the store."
)
optdepends=(
  "${_pub_optdepends[*]}"
)
_tag_name="commit"
_tag="${_commit}"
_tarname="${_pkg}-${_tag}"
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_archive_sum="fe63788c6dad60445c2d613dde484108770d2dadc60be0d6c11f47301c876df0"
_evmfs_archive_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_archive_sum}"
_evmfs_archive_src="${_tarname}.zip::${_evmfs_archive_uri}"
_archive_sig_sum="5ea20db780f7865341eb253ed5e74c4b1623a3c11a9ff90037a98cf4bd1014bf"
_archive_sig_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_archive_sig_sum}"
_archive_sig_src="${_tarname}.zip.sig::${_archive_sig_uri}"
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    "evmfs"
  )
  _src="${_evmfs_archive_src}"
  _sum="${_archive_sum}"
  source+=(
    "${_archive_sig_src}"
  )
  sha256sums+=(
    "${_archive_sig_sum}"
  )
elif [[ "${_git}" == true ]]; then
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
    _sum="${_archive_sum}"
  fi
fi
source+=(
  "${_src}"
)
sha256sums+=(
  "${_sum}"
)
validpgpkeys=(
  # Truocolo <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  'DD6732B02E6C88E9E27E2E0D5FC6652B9D9A6C01'
  # Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
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
  if [[ "${_contracts}" == "true" ]]; then
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
  depends+=(
    "${_pkg}-contracts"
  )
  _make_opts=(
    DESTDIR="${pkgdir}"
    PREFIX='/usr'
  )
  cd \
    "${_tarname}"
  make \
    "${_make_opts[@]}" \
    install-scripts
}

package_ur-docs() {
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
    install-doc
  make \
    "${_make_opts[@]}" \
    install-man
}

