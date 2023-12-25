# This is my local repo


public void generateNotifications() throws IOException, TemplateException {
        // Fetch users and generate notifications
        // This is just a placeholder. In a real application, you would fetch the users from the database and generate a notification for each user.
        List<User> users = new ArrayList<>();
        for (User user : users) {
            Template template = freemarkerConfig.getTemplate("notification.ftl");
            Map<String, Object> model = new HashMap<>();
            model.put("name", user.getName());
            StringWriter writer = new StringWriter();
            template.process(model, writer);

            Notification notification = new Notification();
            notification.setUserId(user.getId());
            notification.setMessage(writer.toString());
            notificationRepository.save(notification);
        }





@Service
public class NotificationProcessorService {

    private final NotificationRepository notificationRepository;

    public NotificationProcessorService(NotificationRepository notificationRepository) {
        this.notificationRepository = notificationRepository;
    }

    public void processNotifications() {
        List<Notification> notifications = notificationRepository.findByProcessedFalse();
        for (Notification notification : notifications) {
            // Process the notification
            // This is just a placeholder. In a real application, you would process the notification and store the result.

            // Mark the notification as processed
            notification.setProcessed(true);
            notification.setResult("Processed notification: " + notification.getMessage());
            notificationRepository.save(notification);
        }
    }
}







@Component
public class NotificationScheduler {

    private final NotificationService notificationService;
    private final NotificationProcessorService notificationProcessorService;

    public NotificationScheduler(NotificationService notificationService, NotificationProcessorService notificationProcessorService) {
        this.notificationService = notificationService;
        this.notificationProcessorService = notificationProcessorService;
    }

    @Scheduled(cron = "0 0 * * * *")  // Run every hour
    public void generateAndProcessNotifications() throws IOException, TemplateException {
        notificationService.generateNotifications();
        notificationProcessorService.processNotifications();
    }
}
