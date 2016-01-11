# Módulos

A arquitetura modular do OpenStack se evidencia pela existência dos seus componentes. Para cada projeto pode-se escolher a implantação de uma combinação de componentes. A sua escolha de componentes pode ter um impacto significativo sobre a concepção global do projeto.

Embora existam certos componentes que estão sempre presentes, como por exemplo o Compute (Nova) e o Serviço de Imagem (Glance), existem outros serviços que podem não precisam estar. Como um exemplo, um certo design pode não requerer o módulo Orchestration. Omitindo Orchestration não teria necessariamente um impacto significativo sobre a concepção global, entretanto, se a arquitetura utiliza um substituto para o OpenStack Object Storage para a sua componente de armazenamento, isso poderia ter impactos significativos sobre o resto do projeto.
