## Iptables reference:
* Manage chains:
    * Create: 
          * `iptables -N new_chain`
    * Edit: 
          * `iptables -E new_chain old_chain`
    * Delete: 
          * `iptables -X old_chain`

* Redirect packet to a user chain:
    * `iptables -A INPUT -p icmp -j new_chain`

* Listing rules:
    * All rules of all tables:
        * `iptables -L`
    * Rules and counters:
        * `iptables -L -v`
    * Specific tables: 
        * `iptables -L -t nat`
    * With line number for all tables 
        * `iptables -L -n --line-numbers`
    * Listing rules with line number for specific table:
        * `iptables -L INPUT -n --line-numbers`

* Manage rules:
    * Append rules to the bottom of the chain 
        * `iptables -A chain`
    * Insert in chain as rulenum (default at the top or 1)
        * `iptables -I chain [rulenum]`
    * Replace rules with rules specified for the rulnum: iptables -R chain rulenum     // 
# iptables -D chain rulenum     // delete rules matching rulenum (default 1)
# iptables -D chain       // delete matching rules

change default policy:
# iptables -P chain target      // change policy on chain to target
# iptables -P INPUT DROP      // change INPUT table policy to DROP
# iptables -P OUTPUT DROP     // change OUTPUT chain policy to DROP
# iptables -P FORWARD DROP      // change FORWARD chain policy to DROP

