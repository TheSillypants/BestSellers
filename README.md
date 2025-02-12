# BestSellers
Our project for COP3076

nyt_data <- read.csv("NYT_best_seller.csv")
view(nyt_data)

glimpse(nyt_data)
colnames(nyt_data)

publisher_counts <- nyt_data %>%
  count(publisher, sort = TRUE)  # Use exact column name from colnames()

# Print the publisher counts
print(publisher_counts)

# Select the top 10 publishers
top_publishers <- publisher_counts %>%
  slice_max(n, n = 10)

# Plot the top publishers
ggplot(top_publishers, aes(x = reorder(publisher, n), y = n)) +
  geom_bar(stat = "identity", fill = "steelblue") +
  coord_flip() +
  labs(title = "Top 10 Publishers in NYT Best Sellers",
       x = "Publisher", 
       y = "Number of Best Sellers") + 
  theme_minimal()

# Plot all publishers 
ggplot(publisher_counts, aes(x = reorder(publisher, n), y = n)) + 
  geom_bar(stat = "identity", fill = "pink") +
  coord_flip() +
  labs(title = "Publishers in NYT Best Sellers",
       x = "Publisher", 
       y = "Number of Best Sellers") + 
  theme_minimal()
