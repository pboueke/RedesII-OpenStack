# Perguntas
---

**1**. Quais são os benefícios da arquitetura modular empregada no OpenStack?

*A arquitetura modular permite a expansão horizontal da camada de infraestrutura em nuvem. Dessa forma o administrador e o implantador do sistema possem uma grande capacidade de adaptar a estrutura funcional de forma a maximizar a eficiência geral, pautados nas métricas que lhe sejam de maior importância.*

**2**. VOLPI

**3**. TK

**4**. THURLER

**5**. Qual a diferença entre um Hypervisor tipo 1 e tipo 2 e o que isso influencia nos *Nós de Computação*?

* Um hypervisor do tipo 2 roda sobre um outro sistema operacional. Um hypervisor tipo 1 roda diretamente no hardware, sem necessidade de um sistema operacional. Portanto ele não pode rodar simultaneamente com um agente do Nova. Portanto é necessário uma máquina dedicada para rodar o Hypervisor enquanto que os nós de computação ficam apenas com o agente do hypervisor. Se apenas forem usados hypervisor do tipo 2 e todos do mesmo tipo, é provável que tenhamos apenas um nó de computação, nos termos do OpenStack, mas teremos vários nós que servem recursos, rodando apenas o hypervisor.
