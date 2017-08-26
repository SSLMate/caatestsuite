# Copyright 2017 Opsmate, Inc.
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

all: expired-dnssec.caatestsuite.com.signed missing-dnssec.caatestsuite.com.signed blackhole-dnssec.caatestsuite.com.signed caatestsuite.com.signed

expired-dnssec.caatestsuite.com.signed: expired-dnssec.caatestsuite.com.
	dnssec-signzone -f $@ -e now+30 -k Kexpired-dnssec.caatestsuite.com.+005+28186.key expired-dnssec.caatestsuite.com. Kexpired-dnssec.caatestsuite.com.+005+53253.key

missing-dnssec.caatestsuite.com.signed: missing-dnssec.caatestsuite.com.
	dnssec-signzone -f $@ -e 20220530144500 -k Kmissing-dnssec.caatestsuite.com.+005+33439.key missing-dnssec.caatestsuite.com. Kmissing-dnssec.caatestsuite.com.+005+41463.key

blackhole-dnssec.caatestsuite.com.signed: blackhole-dnssec.caatestsuite.com.
	dnssec-signzone -f $@ -e 20220530144500 -k Kblackhole-dnssec.caatestsuite.com.+005+04777.key blackhole-dnssec.caatestsuite.com. Kblackhole-dnssec.caatestsuite.com.+005+13938.key

caatestsuite.com.signed: caatestsuite.com. missing-dnssec.caatestsuite.com.signed expired-dnssec.caatestsuite.com.signed
	dnssec-signzone -f $@ -e 20220530144500 -k Kcaatestsuite.com.+005+63892.key caatestsuite.com. Kcaatestsuite.com.+005+62997.key

clean:
	rm -f *.signed dsset-*
