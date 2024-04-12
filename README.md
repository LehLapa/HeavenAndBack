# Heaven And Back - LP
Esse projeto é um jogo criado na game engine Unity. Abordando o tema de céu e inferno, o player irá explorar e interagir com o cenário que trás a temática do caminho da igreja, até os portões do inferno.
## Integrantes 
- Aluna: Letícia da Lapa Silva
- Aluno: Lucas Carvalho

Cursando: ETEC Professor Basilídes de Godoy - Ensino Médio Integrado ao Curso Técnico de Programação de Jogos Digitais. 2ºA/2023
  
## Músicas Utilizadas:
- Highway To Hell by AC/DC (Primeira cena e segunda cena).
- Sanctified With Dynamite by Powerwolf (Primeira cena e segunda cena).

# Diagrama Caso de Uso - Unity
![Diagrama Caso de Uso Unity](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/ff9e6dfe-65b3-41cd-8b2e-30966dd7d7e4)

# Diagrama De Classe - Unity
No Diagrama possuimos a Classe Jogo, que utiliza do atributo Personagem e em seus métodos, ações que iram iniciar e finalizar o jogo. Ao lado esquerdo, temos a Classe Cenário, utilizando como atributos Tamanho, Forma e Posição que mencionam os Assets e Game Objects que serão utilizados no projeto criado no Unity, em seu método, temos a Interação que será utilizada na gameplay. Na Classe Personagem, temos os atributos de Personagem e sua movimentação que será essencial para o jogo, e em seus métodos temos sua movimentação/posição e interação, que será primordial para a exploração na cena.

![Diagrama de Classe Unity](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/ea21e84b-578b-424d-a6fe-85f1242c9f57)

## Requisitos

Para ver essa cena é preciso o Unity com a versão 2021.3.22f1

## Instalação 
1. Clonar o projeto
(Pasta está zipada para preservação do Projeto construído na Unity. Possuindo Scripts no C#, Projeto da Unity e Imagens do Diagrama de Caso de Uso e Diagrama de Classe).
- https://drive.google.com/drive/folders/1hYeF0n-fHcYkPBvFNMxXO6DB6oiEbCTd?usp=sharing
2. Assistir Gameplay disponível no Youtube
- https://youtu.be/aKfdz1C8GKg
3. Abrir o projeto no Unity.

## Desenvolvimento
Para criar esse projeto foram utilizados os seguintes passos:
1. baixar assets na assets store.

- Esses foram os assets baixados para compor a cena do projeto.
  
![Asset Pedra](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/1185a02f-6078-4d9e-9e0a-3de10330c343)
![Asset Portal](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/928c94b4-4344-49e5-b1ab-bfc3f7030ef3)
![Asset Banco](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/01fb7acb-febe-490b-a269-f28066d5f85f)
![Asset Arvore](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/143e8518-fc47-453e-8d68-2a95f28a738c)
![Asset Rua](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/da8fc4ae-274c-46ec-b154-56af2d187303)
![Asset Bar](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/6c92c724-bf1b-4ac5-b112-09a46dbee665)
![Asset Comida](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/731b68b5-6619-43ed-9af8-768523965239)
![Asset Mesa Bar](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/a3199c4d-53a4-4120-ba3c-0f5899fa24c8)
![Asset Lampada](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/9dc86bcf-b540-4816-9753-2174272b1cc4)



- Colocar o personagem que irá receber os scripts.


![Demonio](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/4bceaa93-638c-4d8e-a91b-2845b7cab276)
![Player](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/cd5d5f14-08ce-44d7-baaa-f557f651aed9)



2. Criar os scripts e programar
   Foram usados 3 Scripts para o projeto.

## Controlador de Câmera
  Este script fornece um controlador de câmera no Unity que permite movimento suave e controlado da câmera com base na entrada do mouse. Ele permite que o jogador rotacione a câmera verticalmente e o personagem horizontalmente.
 ![WhatsApp Image 2023-09-17 at 20 05 11](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/d07309e3-18ab-4dd0-b320-a0becf650191)
 
  ## Recursos:
- Rotação vertical da câmera com limite máximo de ângulo

- Rotação horizontal do personagem

- Funcionalidade de bloquear e desbloquear o cursor

- Rotação suave da câmera com base na entrada do mouse

## Como usar:

1. Anexe o script `CameraController` ao objeto da câmera em sua cena do Unity.

2. Atribua o transform da câmera à variável `cameraTransform` no script.

3. Especifique o ângulo vertical máximo que a câmera pode rotacionar no campo `maxVerticalAngle`.

4. Atribua o transform do personagem à variável `body` no script.

5. Ajuste a sensibilidade da rotação da câmera modificando o campo `sensitivity`.

6. Execute o jogo e controle a câmera movendo o mouse.

## Explicação do script:

csharp

using System;

using System.Collections;

using System.Collections.Generic;

using UnityEngine;

public class CameraController : MonoBehaviour

{

public Transform cameraTransform;

public float maxVerticalAngle;

public Transform body;

// Variáveis privadas

private float _mouseVerticalValue;

private float MouseVerticalValue

{

get => _mouseVerticalValue;

set

{

if (value == 0) return;

float verticalAngle = _mouseVerticalValue + value;

verticalAngle = Mathf.Clamp(verticalAngle, -maxVerticalAngle, maxVerticalAngle);

_mouseVerticalValue = verticalAngle;

}

}

public float sensitivity;

// O método Update é chamado uma vez por quadro

void Update()

{

// Captura o movimento vertical do mouse

MouseVerticalValue = Input.GetAxis("Mouse Y");

// Calcula a rotação desejada com base no movimento vertical

Quaternion finalRotation = Quaternion.Euler(

-MouseVerticalValue * sensitivity,

0, 0);

// Aplica a rotação à câmera

cameraTransform.localRotation = finalRotation;

// Rotaciona o personagem horizontalmente com base no movimento do mouse

body.rotation = Quaternion.Euler(

0,

body.localRotation.eulerAngles.y + Input.GetAxis("Mouse X") * sensitivity,

0);

// Bloqueia o cursor e o esconde quando o botão esquerdo do mouse é pressionado

if (Input.GetMouseButtonDown(0))

{

Cursor.lockState = CursorLockMode.Locked;

Cursor.visible = false;

}

// Desbloqueia o cursor e o mostra quando a tecla Esc é pressionada

if (Input.GetKeyDown(KeyCode.Escape))

{

Cursor.lockState = CursorLockMode.None;

Cursor.visible = true;

}

}

}


O script consiste nos seguintes componentes principais:

- *Variáveis Públicas*: Essas variáveis podem ser configuradas no Editor do Unity e permitem a personalização do comportamento do controlador de câmera. Elas incluem `cameraTransform` (o transform da câmera), `maxVerticalAngle` (o ângulo máximo que a câmera pode rotacionar verticalmente), `body` (o transform do personagem

) e `sensitivity` (a sensibilidade da rotação da câmera).

- *Variáveis Privadas*: Essas variáveis são usadas internamente pelo script para controlar o movimento vertical do mouse. `_mouseVerticalValue` armazena o valor acumulado da rotação vertical, e `MouseVerticalValue` é uma propriedade que garante que a rotação vertical fique dentro dos limites especificados.

- *Update()*: Este método é chamado a cada quadro e lida com as atualizações da câmera e entrada do usuário. Ele captura o movimento vertical do mouse, calcula a rotação desejada com base na entrada do mouse e aplica a rotação à câmera e ao personagem. Também verifica a entrada dos botões do mouse e do teclado para bloquear ou desbloquear o cursor e alterar sua visibilidade.Física CC

Este script implementa um controlador de personagem físico no Unity, usando o componente CharacterController. Ele lida com a movimentação do personagem, verificação de colisões e interação com plataformas.

## Recursos:

- Verificação de contato com o solo e cálculo do ângulo do terreno

- Movimentação suave em superfícies inclinadas

- Aplicação de gravidade

- Damping de inércia para desacelerar o personagem em movimento

- Interação com plataformas móveis

- Detecção de colisões e aplicação de força

## Como usar:

1. Anexe o script `PhysicalCC` a um objeto no Unity que possua o componente CharacterController.

2. Personalize os parâmetros no inspector, conforme necessário.

3. Execute o jogo e observe o comportamento do personagem.

## Descrição do Script:

csharp

using System.Collections;

using UnityEngine;

[RequireComponent(typeof(CharacterController))]

public class PhysicalCC : MonoBehaviour

{

public CharacterController cc { get; private set; }

private IEnumerator dampingCor;

[Header("Verificação do Solo")]

public bool isGround;

public float groundAngle;

public Vector3 groundNormal { get; private set; }

[Header("Movimentação")]

public bool ProjectMoveOnGround;

public Vector3 moveInput;

private Vector3 moveVelocity;

[Header("Inércia e Inclinação")]

public float slopeLimit = 45;

public float inertiaDampingTime = 0.1f;

public float slopeStartForce = 3f;

public float slopeAcceleration = 3f;

public Vector3 inertiaVelocity;

[Header("Interação com Plataforma")]

public bool platformAction;

public Vector3 platformVelocity;

[Header("Colisão")]

public bool applyCollision = true;

public float pushForce = 55f;

private void Start()

{

cc = GetComponent<CharacterController>();

}

private void Update()

{

GroundCheck();

if (isGround)

{

moveVelocity = ProjectMoveOnGround ? Vector3.ProjectOnPlane(moveInput, groundNormal) : moveInput;

if (groundAngle < slopeLimit && inertiaVelocity != Vector3.zero) InertiaDamping();

}

GravityUpdate();

Vector3 moveDirection = (moveVelocity + inertiaVelocity + platformVelocity);

cc.Move((moveDirection) * Time.deltaTime);

}

private void GravityUpdate()

{

if (isGround && groundAngle > slopeLimit)

{

inertiaVelocity += Vector3.ProjectOnPlane(groundNormal.normalized + (Vector3.down * (groundAngle / 30)).normalized * Mathf.Pow(slopeStartForce, slopeAcceleration), groundNormal) * Time.deltaTime;

}

else if (!isGround) inertiaVelocity.y -= Mathf.Pow(3f, 3) * Time.deltaTime;

}

private void InertiaDamping()

{

var a = Vector3.zero;

// desaceleração da inércia quando a força do movimento é aplicada

var resistanceAngle = Vector3.Angle(Vector3.ProjectOnPlane(inertiaVelocity, groundNormal),

Vector3.ProjectOnPlane(moveVelocity, groundNormal));

resistanceAngle = resistanceAngle == 0 ? 90 : resistanceAngle;

inertiaVelocity = (inertiaVelocity + moveVelocity).magnitude <= 0.1f ? Vector3.zero : Vector3.SmoothDamp(inertiaVelocity, Vector3.zero, ref a, inertiaDampingTime / (

3 / (180 / resistanceAngle)));

}

private void GroundCheck()

{

if (Physics.SphereCast(transform.position, cc.radius, Vector3.down, out RaycastHit hit, cc.height / 2 - cc.radius + 0.01f))

{

isGround = true;

groundAngle = Vector3.Angle(Vector3.up, hit.normal);

groundNormal = hit.normal;

if (hit.transform.tag == "Platform")

platformVelocity = hit.collider.attachedRigidbody == null | !platformAction ?

Vector3.zero : hit.collider.attachedRigidbody.velocity;

if (Physics.BoxCast(transform.position, new Vector3(cc.radius / 2.5f, cc.radius / 3f, cc.radius / 2.5f),

Vector3.down, out RaycastHit helpHit, transform.rotation, cc.height / 2 - cc.radius / 2))

{

groundAngle = Vector3.Angle(Vector3.up, helpHit.normal);

}

}

else

{

platformVelocity = Vector3.zero;

isGround = false;

}

}

private void OnControllerColliderHit(ControllerColliderHit hit)

{

if (!applyCollision) return;

Rigidbody body = hit.collider.attachedRigidbody;

// verificar rigidbody

if (body == null || body.isKinematic) return;

Vector3 pushDir = hit.point - (hit.point + hit.moveDirection.normalized);

// aplicar força de empurrão

body.AddForce(pushDir * pushForce, ForceMode.Force);

}

}


O script consiste nos seguintes componentes principais:

- *Variáveis Públicas*: Essas variáveis podem ser configuradas no Editor do Unity e controlam o comportamento do controlador de personagem físico. Elas incluem `cc` (uma referência ao CharacterController), `isGround` (uma flag indicando se o personagem está no chão), `groundAngle` (o ângulo do terreno), `groundNormal` (o vetor normal do terreno), `moveInput` (o input de movimento), `slopeLimit` (o limite de inclinação em que o personagem pode se mover), `inertiaDampingTime` (o tempo de desaceleração da inércia), `slopeStartForce` (a força inicial ao subir uma rampa) e `applyCollision` (uma flag indicando se a colisão deve ser aplicada).

- *Métodos Update() e GravityUpdate()*: O método `Update()` é chamado a cada quadro e lida com a movimentação do personagem. Ele chama outros métodos para verificar o contato com o solo, atualizar a gravidade, aplicar a inércia e interagir com plataformas. O método `GravityUpdate()` calcula a força de gravidade aplicada ao personagem com base na inclinação do terreno.

- *Métodos InertiaDamping() e GroundCheck()*: O método `InertiaDamping()` desacelera a inércia do personagem quando uma força de movimento é aplicada. O método `GroundCheck()` verifica se o personagem está no chão, calcula o ângulo do terreno e armazena o vetor normal do terreno.

- *Método OnControllerColliderHit()*: Esse método é chamado quando o controlador de personagem colide com outro objeto. Ele verifica se há uma colisão aplicável e adiciona uma força de empurrão ao objeto colidido.

## Entrada do Player

![WhatsApp Image 2023-09-17 at 20 04 33](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/96129e93-ffa1-470c-95dc-4dc1d6720c9f)


Este script controla a entrada do jogador no Unity. Ele lida com o movimento do jogador, saltos e ação de sentar-se.

## Recursos:

- Movimento suave baseado na entrada do jogador

- Salto controlado pelo pressionamento da tecla de espaço

- Ação de sentar-se ao pressionar a tecla C

## Como usar:

1. Anexe o script `PlayerInput` a um objeto no Unity que represente o jogador.

2. Certifique-se de ter um componente `PhysicalCC` anexado ao objeto do jogador.

3. Atribua a referência do componente `PhysicalCC` à variável `physicalCC` no inspector.

4. Opcionalmente, configure as variáveis `speed` (velocidade do jogador) e `jumpHeight` (altura do salto) no inspector.

5. Se necessário, ajuste a variável `bodyRender` para a renderização do corpo do jogador no inspector.

6. Execute o jogo e teste o movimento, saltos e ação de sentar-se do jogador.

## Descrição do Script:

csharp

using System.Collections;

using UnityEngine;

public class PlayerInput : MonoBehaviour

{

public float speed = 5;

public float jumpHeight = 15;

public PhysicalCC physicalCC;

public Transform bodyRender;

private IEnumerator sitCort;

private bool isSitting;

private void Update()

{

if (physicalCC.isGround)

{

physicalCC.moveInput = Vector3.ClampMagnitude(transform.forward * Input.GetAxis("Vertical") +

transform.right * Input.GetAxis("Horizontal"), 1f) * speed;

if (Input.GetKeyDown(KeyCode.Space))

{

physicalCC.inertiaVelocity.y = 0f;

physicalCC.inertiaVelocity.y += jumpHeight;

}

if (Input.GetKeyDown(KeyCode.C) && sitCort == null)

{

sitCort = sitDown();

StartCoroutine(sitCort);

}

}

}

private IEnumerator sitDown()

{

if (isSitting && Physics.Raycast(transform.position, Vector3.up, physicalCC.cc.height * 1.5f))

{

sitCort = null;

yield break;

}

isSitting = !isSitting;

float t = 0;

float startSize = physicalCC.cc.height;

float finalSize = isSitting ? physicalCC.cc.height / 2 : physicalCC.cc.height * 2;

Vector3 startBodySize = bodyRender.localScale;

Vector3 finalBodySize = isSitting ? bodyRender.localScale - Vector3.up * bodyRender.localScale.y / 2f : bodyRender.localScale + Vector3.up * bodyRender.localScale.y;

speed = isSitting ? speed / 2 : speed * 2;

jumpHeight = isSitting ? jumpHeight * 3 : jumpHeight / 3;

while (t < 0.2f)

{

t += Time.deltaTime;

physicalCC.cc.height = Mathf.Lerp(startSize, finalSize, t / 0.2f);

bodyRender.localScale = Vector3.Lerp(startBodySize, finalBodySize, t / 0.2f);

yield return null;

}

sitCort = null;

yield break;

}

}


O script consiste nos seguintes componentes principais:

- *Variáveis Públicas*: Essas variáveis podem ser configuradas no Editor do Unity e controlam o comportamento da entrada do jogador. Elas incluem `speed` (velocidade do jogador)

e `jumpHeight` (altura do salto). A variável `physicalCC` deve ser atribuída com uma referência ao componente `PhysicalCC` que lida com a física do personagem.

- *Variáveis Privadas*: Essas variáveis são usadas internamente pelo script para controlar a ação de sentar-se. A variável `bodyRender` é opcional e pode ser configurada para a renderização do corpo do jogador.

- *Método Update()*: O método `Update()` é chamado a cada quadro e lida com a entrada do jogador. Se o jogador estiver no chão, a entrada é usada para controlar o movimento do jogador e o salto. O movimento é definido em `physicalCC.moveInput` e o salto é ativado definindo `physicalCC.inertiaVelocity.y` como a altura do salto.

- *Método sitDown()*: O método `sitDown()` é uma rotina que lida com a ação de sentar-se do jogador. Ele ajusta a altura do personagem e a escala do corpo gradualmente para criar uma animação suave. A velocidade e altura do salto também são ajustadas com base no estado de sentar-se.
  
## NPC Follow Script
O NPC Follow Script é um script simples em C# para Unity que permite que um NPC siga um alvo (por exemplo, um jogador) em um jogo. Este script pode ser usado para criar comportamentos de perseguição de personagens não jogáveis (NPCs) em seu jogo.


## Funcionalidades:
Permite que um NPC siga um alvo (como um jogador) em uma cena.
Ajuste a velocidade de movimento do NPC para controlar a rapidez com que ele segue o alvo.
O NPC pode ser configurado para olhar sempre na direção do alvo.
Requisitos
Este script é projetado para ser usado em um projeto Unity. Você deve ter o Unity instalado para usá-lo.
Como Usar
Importação do Script: Copie o código do script e cole-o em um arquivo C# no seu projeto Unity.

Vincule o Alvo: No Unity, selecione o NPC que você deseja que siga um alvo. No Inspector, você verá uma seção chamada "NPC Follow". Arraste o objeto que deseja que o NPC siga para o campo "Target".

Ajuste a Velocidade: Você pode ajustar a velocidade de movimento do NPC ajustando o valor no campo "Move Speed". Isso controlará o quão rápido o NPC segue o alvo.

Opcional: Olhar para o Alvo: Se desejar que o NPC sempre olhe na direção do alvo, marque a opção "Look At Target" no Inspector.

Execute o Jogo: Execute o jogo no Unity e observe como o NPC segue o alvo configurado.

using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class NPCFollow : MonoBehaviour
{
    public Transform target; // O alvo que o NPC deve seguir
    public float moveSpeed = 5.0f; // Velocidade de movimento do NPC

    private void Update()
    {
        if (target != null)
        {
            // Calcula a direção para o alvo
            Vector3 direction = (target.position - transform.position).normalized;

            // Move o NPC na direção do alvo
            transform.Translate(direction * moveSpeed * Time.deltaTime);

            // Rotaciona o NPC para enfrentar o alvo (opcional)
            transform.LookAt(target);
        }
    }
}



## Mudar de fase
O Mudar de Fase é um script Unity simples em C# que permite que você mude de uma cena para outra pressionando uma tecla (por exemplo, a tecla "E"). Este script pode ser usado para criar transições de fase ou níveis em seu jogo.
![WhatsApp Image 2023-09-17 at 20 03 34](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/85b2d218-cd70-4f10-877c-f58233ceb95f)

![WhatsApp Image 2023-09-17 at 20 05 39](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/a8e7414f-5bac-4be0-baa1-f5318e6bdee9)

![WhatsApp Image 2023-09-17 at 20 05 24 (1)](https://github.com/LehLapa/HeavenAndBack-LP/assets/128638269/db85d533-27a2-4c18-970b-1574ceb2bf9f)


## Funcionalidades:
Carrega uma cena específica quando a tecla designada é pressionada (por padrão, a tecla "E").
Pode ser personalizado para carregar qualquer cena do seu projeto Unity.
Requisitos
Este script é projetado para ser usado em um projeto Unity. Você deve ter o Unity instalado para usá-lo.
Como Usar
Importação do Script: Copie o código do script e cole-o em um arquivo C# no seu projeto Unity.

Vincule a Cena de Destino: Abra o script no Inspector e insira o nome da cena que você deseja carregar no campo "Scene Name" (Nome da Cena).

Ajuste a Tecla de Ativação: Por padrão, o script é configurado para carregar a cena quando a tecla "E" for pressionada. Você pode ajustar essa tecla modificando a linha if (Input.GetKeyDown(KeyCode.E)).

Execute o Jogo: Execute o jogo no Unity e, quando estiver na cena onde deseja ativar a transição, pressione a tecla especificada para mudar para a cena de destino.

using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.SceneManagement;

public class MudarFase : MonoBehaviour
{
    void Update()
    {
        // Verifica se a tecla "E" foi pressionada.
        if (Input.GetKeyDown(KeyCode.E))
        { 
            CarregarFase(); // Chama a função para carregar a cena.
        }
    }

    private void CarregarFase()
    {
        // Carrega a cena com o nome "fase2". Substitua "fase2" pelo nome da sua cena de destino.
        SceneManager.LoadScene("fase2");
    }
}










