# Priorização Orientada a Negócios de Dívidas Técnicas


A dívida técnica é identificada por um nome e descrição, além de possuir uma prioridade técnica e um risco associado (probabilidade de impactar áreas do sistema). É importante diferenciar a dívida técnica de um incidente. Um incidente é um evento que já está ocorrendo, como um bug que está causando problemas no sistema, resultando em indisponibilidade ou funcionalidades inativas. Embora um incidente não seja uma dívida técnica em si, pode ser originado por uma dívida técnica existente. Além disso, um incidente pode dar origem a uma nova dívida técnica.

As dívidas técnicas podem ser encontradas em componentes, que também são conhecidos como itens de configuração. Um componente pode ser um módulo do sistema ou um artefato, como um banco de dados, serviço ou aplicação. Tudo o que é técnico é considerado um componente. Os componentes possuem três atributos: operational (em operação), to-be operational (em desenvolvimento/planejamento) e legacy (legado). Com base nisso, concluímos que uma dívida técnica presente em um componente afeta uma funcionalidade específica.

Algumas observações importantes: se um componente é descontinuado, a dívida técnica associada a ele é eliminada.

A compreensão desses conceitos também envolve os usuários. O sistema (no caso, o e-commerce) pode ser considerado um produto, também conhecido como It Asset. O produto possui várias funcionalidades, cada uma com duas propriedades: Core-business ou No-Core. Em geral, o Core-business refere-se às funcionalidades essenciais que definem o produto, ou seja, são suas principais características. Já o No-Core se refere a funcionalidades que fazem parte do produto, mas estão fora do fluxo principal. Mesmo sem essas funcionalidades, o produto ainda pode ser utilizado. Outro atributo é a usage, que indica o quanto uma funcionalidade é utilizada. Funcionalidades com alta utilização são classificadas como high, enquanto aquelas com menor utilização são classificadas como low.

Compreendendo esses conceitos, podemos estabelecer uma política de priorização para a Tracy-td. Essa política leva em consideração os valores, a utilização e o estado da funcionalidade. Vamos utilizar um exemplo para ilustrar melhor: uma dívida técnica que possui o value Core-Business (uma funcionalidade essencial para o fluxo principal do produto), uma usage High (alta taxa de utilização) e está no estado operational (em operação/produção). Essa dívida técnica receberia a prioridade mais alta, classificada como 1. Da mesma forma, outras dívidas técnicas seriam classificadas com valores de 1 a 10, levando em conta seus atributos. É importante ressaltar que a classificação dos valores é definida pelas empresas e esse é apenas um exemplo para facilitar o entendimento.



Entendendo Conceitos:

Features (fonte de valor) / Funcionalidades: São as diferentes partes do sistema que agregam valor aos usuários.

Business Value: Representa o valor que uma funcionalidade agrega ao negócio.

Core-Business: Refere-se às funcionalidades essenciais do sistema, aquelas que fazem parte do fluxo principal do produto.

No-Core-Business: São funcionalidades que estão fora do fluxo principal, mas ainda fazem parte do produto.

Usage: Indica o nível de utilização de uma funcionalidade pelos usuários. Pode ser classificado como high (alto) ou low (baixo), dependendo da taxa de utilização.

Value: Representa o valor atribuído a uma funcionalidade com base em critérios como Business Value, Core-Business, No-Core-Business e Usage.

Operational (Está em operação/em produção): Refere-se ao estado de uma funcionalidade que está ativa e em pleno funcionamento.

To-be operational (Está sendo desenvolvido/em planejamento): Indica que uma funcionalidade está em processo de desenvolvimento ou em fase de planejamento.

Legacy (Sistema Legado): Refere-se a um sistema que já possui uma data definida para ser desativado, geralmente substituído por uma nova versão ou tecnologia.

