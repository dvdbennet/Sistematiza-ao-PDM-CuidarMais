# Sistematiza-ao-PDM-CuidarMais
Sistematização da matéria de Programação para Dispositivos Móveis
--
# David Nora Bennet - RA: 72401665

# Cuidar Mais - Aplicativo de Gerenciamento de Medicamentos

## Visão Geral

O Cuidar Mais é um aplicativo móvel desenvolvido em React Native (Expo) para ajudar usuários a gerenciar seus medicamentos diários.

## Funcionalidades Implementadas

### 1. Tela "Medicamentos" (`app/(tabs)/medicines.tsx`)

- Adicionar novos medicamentos com nome e seus horários
- Visualizar todos os medicamentos cadastrados
- Excluir medicamentos com confirmação
- Validação de formato de horário (HH:MM)

### 2. Tela "Hoje" (`app/(tabs)/today.tsx`)

- Visualiza todos os horários de medicamentos para o dia atual
- Mostra data e hora atual
- Permite marcar medicamentos como tomados
- Registra o horário real em que o medicamento foi tomado

### 3. Tela "Histórico" (`app/(tabs)/history.tsx`)

- Visualiza histórico completo de medicamentos tomados
- Agrupa registros por data
- Mostra horário previsto vs horário real
- Permite excluir registros do histórico com confirmação
- Diferencia "Hoje" e "Ontem" nas datas

## Estrutura de Dados


```typescript
{
  id: string;
  name: string;
  times: string[]; // ["08:00", "20:00"]
}
```

### HistoryEntry

```typescript
{
  id: string;
  medicineId: string;
  medicineName: string;
  scheduledTime: string; // Horário previsto
  takenAt: string; // ISO timestamp do momento real
}
```

## Armazenamento

- **AsyncStorage** do React Native para persistência local
- Chaves utilizadas:
  - `@cuidarmais:medicines` - Lista de medicamentos
  - `@cuidarmais:history` - Histórico de medicamentos tomados

## Arquivos Principais

- `types/medicine.ts` - Definições de tipos TypeScript
- `utils/storage.ts` - Funções de persistência de dados
- `app/(tabs)/medicines.tsx` - Tela de gerenciamento de medicamentos
- `app/(tabs)/today.tsx` - Tela de medicamentos do dia
- `app/(tabs)/history.tsx` - Tela de histórico
- `app/(tabs)/_layout.tsx` - Configuração de navegação por abas

## Como Usar

1. **Adicionar Medicamento**:

   - Vá para a aba "Medicamentos"
   - Digite o nome do medicamento
   - Adicione os horários (formato 24h: HH:MM)
   - Toque em "Salvar Medicamento"

2. **Marcar como Tomado**:

   - Vá para a aba "Hoje"
   - Encontre o medicamento e horário
   - Toque em "✓ Tomado"
   - Confirme a ação

3. **Revisar Histórico**:
   - Vá para a aba "Histórico"
   - Visualize todos os registros agrupados por data
   - Exclua registros se necessário (com confirmação)

## Interface

- Totalmente em **Português**
- Suporte a temas claro e escuro
- Design responsivo e intuitivo
- Confirmações para ações destrutivas

## Executar o Aplicativo

```bash
# Iniciar o servidor de desenvolvimento
npm start

# Para Android
npm run android

# Para iOS
npm run ios
```

## Video no YouTube
- https://youtu.be/3e-0WhJu_Ok
