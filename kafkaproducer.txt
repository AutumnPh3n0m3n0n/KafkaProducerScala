import org.apache.kafka.clients.producer._



object simple_producer {
  def main(args: Array[String]): Unit = {


    val topicName = "sharath_kafka"
    val key = "Key2"
    val value = "My name is Sharath"
    val props = new Properties()
    props.put("bootstrap.servers", "localhost:9092, localhost:9093, localhost:9094")
    props.put("key.serializer", "org.apache.kafka.common.serialization.StringSerializer")
    props.put("value.serializer", "org.apache.kafka.common.serialization.StringSerializer")
    val producer = new KafkaProducer[String, String](props)
    val record = new ProducerRecord[String, String](topicName, key, value)
    producer.send(record)
    producer.close()
    System.out.println("Simple Producer Completed")
  }
}