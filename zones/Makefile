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

all: missing.caatestsuite-dnssec.com.signed expired.caatestsuite-dnssec.com.signed caatestsuite-dnssec.com.signed

missing.caatestsuite-dnssec.com.signed: missing.caatestsuite-dnssec.com.
	named-checkzone -o $@ missing.caatestsuite-dnssec.com. missing.caatestsuite-dnssec.com.

expired.caatestsuite-dnssec.com.signed: expired.caatestsuite-dnssec.com.
	dnssec-signzone -f $@ -e now+30 -k Kexpired.caatestsuite-dnssec.com.+005+54799.key expired.caatestsuite-dnssec.com. Kexpired.caatestsuite-dnssec.com.+005+20931.key

caatestsuite-dnssec.com.signed: caatestsuite-dnssec.com.
	dnssec-signzone -f $@ -e 20220530144500 -k Kcaatestsuite-dnssec.com.+005+58522.key caatestsuite-dnssec.com. Kcaatestsuite-dnssec.com.+005+62745.key

clean:
	rm -f *.signed dsset-*
