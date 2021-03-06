# Группы размещения

При создании виртуальные машины автоматически распределяются по физическому оборудованию Яндекс.Облака. Чтобы контролировать уровень отказоустойчивости оборудования, виртуальные машины можно объединять в группы размещения.

_Группа размещения_ — группа виртуальных машин, каждая из которых расположена на физическом оборудовании согласно определенной стратегии. {{ compute-full-name }} использует стратегию распределенного размещения.

_Распределенное размещение_ (`spread`) — стратегия размещения виртуальных машин таким образом, чтобы каждая из виртуальных машин была гарантированно расположена на отдельной серверной стойке в одной из зон доступности. Если одна из стоек выйдет из строя, другие продолжат работу в обычном режиме.

![image](../../_assets/compute/placement-groups.svg)

Объединение виртуальных машин в группу по стратегии распределенного размещения обеспечивает высокий уровень отказоустойчивости и снижает риск одновременного выхода из строя виртуальных машин, расположенных на одной серверной стойке. Однако, из-за жестких требований к размещению, вероятность нехватки физических ресурсов для виртуальных машин, объединенных в группу размещения, выше, в сравнении с тем же количеством машин, не объединенных в группу.

Ознакомиться с организационными и техническими ограничениями групп размещения можно в разделе [Квоты и лимиты](../concepts/limits.md).

## Смотрите также {#see-also}

* [Как создать группу размещения](../operations/placement-groups/create.md).
* [Как добавить виртуальную машину в группу размещения](../operations/placement-groups/add-vm.md).
* [Как создать виртуальную машину в группе размещения](../operations/placement-groups/create-vm-in-pg.md).