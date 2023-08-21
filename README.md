# Flex_Generation

## Code Development

### Namespace

预测当前可连接位点 **gen**: y_protein_frontier_pred/y_frontier_pred; **real**: idx_focal 

预测下一个原子的位置 **gen**: relative_pos_mu; **real**: pos_query (data['next_site_attach_pos'])

预测下一个片段/原子的类型: **gen**: y_cls; **real**: next_motif_mol 

预测下一个连接点: **gen**: next_site_pred; 

预测连接键的类型 **gen**: bond_pred; **real**: data['next_bond']

预测下一个片段/原子的位置: **gen**: updated_pos; **real**: compose_pos_next_target





