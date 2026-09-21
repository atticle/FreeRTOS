# Thread
```c
osThreadId_t taskHandle;
const osThreadAttr_t task_attributes = {
  .name = "task",
  .priority = (osPriority_t) osPriorityNormal,
  .stack_size = 256 * 4
};
 
taskHandle = osThreadNew(Task, NULL, &task_attributes)

void Task(void *argument)
{
   for(;;)
   {
   }
}
```

# MessageQueue
```c
osMessageQueueId_t queueHandle;

typedef struct {
    uint8_t cmdType;
    uint32_t value;
} queueMessage;

queueHandle = osMessageQueueNew(4, sizeof(queueMessage), NULL);

osMessageQueuePut(queueHandle, &msg, 1U, 0U);

uint8_t msgPrio;
osMessageQueueGet(queueHandle, &msg, &msgPrio, osWaitForever);
```

# Semaphore
```c
osSemaphoreId_t semaHandle;
semaHandle = osSemaphoreNew(1U, 0U, NULL);

osSemaphoreAcquire(semaHandle, osWaitForever);
osSemaphoreRelease(semaHandle);
```

# Mutex
```c
osMutexId_t mutexHandle;
mutexHandle = osMutexNew(NULL);

osMutexAcquire(mutexHandle, 20U);
osMutexRelease(mutexHandle);
```

# Soft Timer
````c
osTimerId_t timerHandle;

timerHandle = osTimerNew(TimerCallback, osTimerPeriodic, NULL, NULL)
osTimerStart(timerHandle, MillisecondsToKernelTicks(500U))

void TimerCallback(void *argument)
{
   for(;;)
   {
   }
}
```

-----------------------------------------------------------------------
